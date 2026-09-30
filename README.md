# STM32 ADC-DAC Learning Project (NUCLEO-F446RE)

A step-by-step embedded systems project exploring the ADC and DAC peripherals of the STM32F446RE using STM32CubeIDE and the HAL library. Each learning step lives in its own Git branch, building on the previous one.

## Hardware & Tools

- **Board:** NUCLEO-F446RE (STM32F446RET6, Cortex-M4)
- **IDE:** STM32CubeIDE
- **Drivers:** STM32 HAL
- **Serial terminal:** any COM terminal (115200 baud, 8N1)
- **Extras:** potentiometer(s) and/or resistors for a voltage divider

## Repository Structure

| Branch | Step / Focus Area | Key Features |
|---|---|---|
| `main` | Baseline release | Core project setup and stable main build. |
| `feature/adc-dma-multichannel` | **Step 1:** Multi-channel DMA | Multi-channel regular scan mode using DMA for zero-CPU sampling overhead. |
| `feature/adc-watchdog` | **Step 2:** Analog Watchdog | Hardware-level window voltage monitoring (AWD) triggering real-time alarm flags on threshold breaches. |
| `feature/dac-adc-loopback` | **Step 3:** DAC signal generation & internal sensors | DAC output on PA4 for testing and loopback signal calibration; internal VREFINT and temperature sensor channels added to the DMA scan. |
| `moving-average-filter` | **Step 4:** Software filtering | Moving average digital filter on circular DMA data for signal stabilization and smoother voltage readings. |
| `feature/dual-adc-mode` | **Step 5:** Dual ADC simultaneous mode | Hardware-synchronized Master (ADC1) / Slave (ADC2) simultaneous sampling with packed 32-bit DMA transfers. |

## Pin Mapping

| Signal | Pin | Notes |
|---|---|---|
| ADC1 Channel 0 | PA0 (A0) | Analog input, e.g. potentiometer wiper |
| ADC1 Channel 1 | PA1 (A1) | Analog input, e.g. second potentiometer or voltage divider |
| DAC Channel 1 | PA4 | Analog output |
| USART2 TX/RX | PA2 / PA3 | Routed to the ST-Link virtual COM port (USB) |

**Wiring:** connect each potentiometer between **3.3V** and **GND**, with the wiper to A0 (or A1). Do **not** use the 5V pin; the ADC inputs are not 5V tolerant.
