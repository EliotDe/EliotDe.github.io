---
layout: default
title: About my Embedded Project
---

# About my Embedded Project

## Motivation

Computer systems aren't of much use until they interact with the world. Unsuprisingly the most obivous interactions are human-computer interactions; usually achieved by reading keystrokes and disseminating some information to a GUI. However, computers are increasingly interacting with the world more directly: sensing and actuating. Having most of my time making the first kind of computer system, I wanted to make something more practical. And, given the rapid growth of the IoT and the attention it is receiving, I wanted to learn about embedded systems and making an IoT device. 

I have decided to go completely baremetal for this project which means I don't use any HAL libraries, additionally I avoid using stdlib functions and I've used VSCode (and occasionally a text editor), a linker script and a makefile rather than using STM32s IDE. This forces me to really understand my components by reading the datasheets, reference manuals and schematics myself (STM32s IDE provides information like this in the app) as well as understanding my code and exactly how it interacts with the MCU.

The goal is to eventually to join the things network (TTN) and the LoRaWAN.

## Learning by Doing

This project is also a way for me to learn low-level programming. As such you can see that I approach things differently throughout the project. An obvious example is naming conventions:

```
void main(){
  ...
  uint8_t usart_config_retval = Manager_USART_Config(USART_MODE_POLLING);
  ...
  manager_retval = sensor_manager_init();
```

Beyond stylistic changes I learn better Embedded-C practices as I progress through the project

## Design

I have divided my project into drivers, managers (which act as my own HAL) and application code. I have tried to make everything as self-contained as possible, my drivers are completely self contained, managers interact with many drivers and the main application interacts with many managers. The only exception is the BME280 driver which uses pointers to SPI read and write functions. This modularity has made it easier for me to diagnose issues and refactor.

## Debugging Manager

The debugging manager is simple. It configures the relevant GPIO pins and passes a buffer to the USART driver to write. My board has a bridge between USART pins and the ST-Link for easy debugging, but it also works with a UART-USB adapter.

## Sensor Manager

The sensor manager essentially configures the clocks and gpio pins for SPI transfers and the BME280 and SPI drivers. The read process is illustrated below. It is not completely accurate -- there are intermediate steps -- but it does capture the process in general. The sensor manager initiates the BME280 and passes the bme280_dev struct; this struct contains pointers to the spi_read, spi_write and delay functions. Polling functions are used since the stm32 wakes up every five minutes and only makes short transfers to the bme280: usually one byte (two including the address) except for burst writes or reading sensor data (usually around 8 bytes). The BME280 calls read/write wrappers in the sensor manager, which have the expected function signatures, and the manager then calls the corresponding driver function. The BME280 driver and SPI driver never call one another.

## Pinout

SPI1_MOSI -> PA7
SPI1_MISO -> PA6
SPI1_SCK  -> PA5
SPI1_NSS  -> PA4
USART2_TX -> PA2








