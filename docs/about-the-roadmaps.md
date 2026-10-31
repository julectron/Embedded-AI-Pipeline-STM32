# 1. Embedded AI Roadmap (System Architecture Deep Dive)

This document represents my personal mental model and system design approach for implementing an Embedded AI pipeline on STM32. It serves as a high-level explanation of the C++ pipeline architecture.

## Stage 1: Configuration
The first step is the hardware and peripheral configuration. This includes:
- Defining and enabling the necessary peripherals used in the architecture.
- Enabling or disabling specific hardware interrupts (IRQs).
- Verifying the hardware data path and routing.

## Stage 2: Preprocessing
In this stage, the raw data is prepared for processing. It includes:
- Defining the necessary memory buffers.
- Establishing the communication mechanisms between peripherals.
- Calculating the optimal buffer size.
- **Crucial Focus:** Attention to `Data Path`, `Data Flow`, `Data Consistency`, `Data Integrity`, `Ownership`, `Data Contract`, `Data Insurance`, and `Data Lifetime`. 
*(I will elaborate on these critical concepts in future documents).*

## Stage 3: Feature Extraction & Processing
*Note: Feature extraction can technically sit between preprocessing and processing. However, in my specific architecture, I have grouped it within the processing stage.*

This stage involves complex mathematical operations. The most **critical rule** here is:
> **"The data extracted and processed here MUST match and align perfectly with the data format expected by the TinyML model."**
If these data formats do not match, the entire system will fail to operate correctly.

## Stage 4: Defining the Threshold
This is the final stage of the primary pipeline. Here, we define the criteria (the threshold) against which the system's output will be compared to make the final real-time decision. 

## Why this Architecture Matters
While many tutorials focus solely on running a model on a microcontroller, this architecture emphasizes the **System Design** behind it. Understanding the data path, buffer lifetimes, and feature alignment is what separates a fragile prototype from a robust, industrial-grade embedded system.

---
*Stay tuned: In the next document, I will explain the TinyML pipeline (Python side) and how it converges with this C++ pipeline.*
