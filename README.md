# SENTINEL: Securely Executing New Technology ICs Near Electromagnetic Listeners (Project 5)

## By: (Marc Chmielewski)·(James Arnold)

## Project Outline

### Objectives
The objective of this project is to develop a machine-learning-driven approach to the characterization of electromagnetic fault injection (EMFI) signals, from “bad actor” chiplets, in heterogeneous systems. 

As reliance on the global supply chain increases, there exist several advanced, and potentially persistent, threats from bad actors, be they foreign governments, other corporations, organized crime, or even vengeful former employees that could compromise the function of or intellectual property associated with a microelectronic device. While motivations may vary, it is imperative that we develop a system by which to detect exploitation techniques, such as EMFI, so that we can respond in a fail-safe manner. At the very least, this means falling into a position where IP cannot be compromised and ideally if it is safe to do so, terminate the operation of the chip for the duration of the attack.

We intend to implement this behavior through the deployment of an onboard voltage sensing suite within the power-distribution network (PDN). This suite will utilize half-space trees to identify anomalies within the stream of voltage sensor data, and from this information determine if the anomaly is indicative of malicious behavior. Ideally, this detector will be able to further classify the nature of the attack and allow the chip to fail into a safe state.

### Work Plan
Before attempting to categorize any behavior or develop an algorithm, it will be essential to better understand the problem we are tasked with.  First, we must analyze the sensors that may be used to detect EM noise to determine how they can monitor EM radiation, and what information can be inferred from these readings.  With a general background understanding, we can investigate the specific noise produced by ring oscillators pulling power from a PDN in an isolated system, and characterize this noise source so that it can be uniquely identified from other sources of noise.

Once this basic background information is collected, it will be possible to design/implement monitors that are capable of collecting information on the EM noise on the power distribution network but cannot yet make sense of that information.  These monitors will allow us to study the impact of a variety of ring oscillator characteristics on the network, including quantity, size, distance/location.  Importantly we will attempt to distinguish between each of these factors so that a large RO farther away is discernible from a small RO closer to the sensor.  This may introduce the need for new design decisions such as placing two sensors that can “triangulate” distance along the PDN.

Additionally, we can evaluate how attacks like FPGAhammer occur and identify patterns in RO behavior that may allow us to identify an RO-based voltage drop attack.  Combining this with our study of RO characteristics and their impact on the PDN, we can begin to identify what attacks might look like on the PDN.  This would potentially allow for the identification of these attacks by simply monitoring the PDN and actively analyzing the data with a machine learning package such as skmultiflow, which has tools for using HS trees to identify anomalies in continuous streams of data.

### Expected Results
We expect that we will be able to accurately identify RO characteristics on an otherwise noiseless network, and will be able to produce an ML algorithm that can parse this information to a high degree of accuracy.  Further, we expect that we will be able to maintain a reasonable degree of accuracy on a PDN with realistic amounts of other noise.  We believe that this will allow us to identify known patterns that may indicate a voltage drop attack, and we hope that we may be able to extend this to more general detection, although that is a “stretch” goal.

## Timeline

Feb 11 (three weeks): finish reading on ring oscillators, voltage-drop attacks, and the relationship between the two

Feb 25 (two weeks): finish setting up simulations of a simple RO on a PDN, and analyze results

Mar 18 (three weeks): extend simulations to characterize various RO parameters and their impact on a PDN (size, location, quantity, etc), may blend with the next goal if ML identification is necessary (due to difficulty of manual recognition)

April 1 (two weeks): automatic ML identification of the specified RO characteristics, may blend with the previous goal

April 13 (two weeks): identification of potential voltage drop attacks (stretch goal)

## References

Jonas Krautter, Dennis Gnad, and Mehdi Tahoori, “FPGAhammer: Remote Voltage Fault Attacks on Shared FPGAs, suitable for DFA on AES” IACR Transactions on Cryptographic Hardware and Embedded Systems, vol. 2018, No. 3, pp. 44-68, 2018.

Sonia Dhia, Alexandre Boyer, Bertrand Vrignon, Mikaël Deobarro, and Thanh Vinh Dinh,
“On-chip noise sensor for integrated circuit susceptibility investigations.” IEEE
Transactions on Instrumentation and Measurement, vol. 61, pp. 696-707, 2011.

Falk Schellenberg, Dennis Gnad, Amir Moradi, and Mehdi B. Tahoori, “Remote inter-chip
power analysis side-channel attacks at board-level.” In Proceedings of the IEEE/ACM
International Conference on Computer-Aided Design (ICCAD) , 2018.

Mark Zhao and G. Edward Suh, “FPGA-based remote power side-channel attacks.” In
Proceedings of the IEEE Symposium on Security and Privacy (SP), pp. 229-244, 2018.

Ilias Giechaskiel, Kasper B. Rasmussen, and Ken Eguro, “Leaky Wires: Information
Leakage and Covert Communication Between FPGA Long Wires.” In Proceedings of the
ACM Asia Conference on Computer and Communications Security, pp. 15-27, 2018.

Dennis Gnad, Fabian Oboril, and Mehdi B. Tahoori, “Voltage drop-based fault attacks on
FPGAs using valid bitstreams.” In Proceedings of the International Conference on Field
Programmable Logic and Applications (FPL), pp. 1-7, 2017.
