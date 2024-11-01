# Recruits Task - Week #2
- ## [git para noobs](https://hackmd.io/@PedroRomao/HJ0GJSae1x)
- ## Add this file to your local git repository create a new branch and work on it, when you are done or as you complete the questions merge the branch into the main branch (remote main branch will have your final work, this means main branch on GitHub, please make the repository public for the next weeks).
- ## Perform the following tasks to the best of your hability, sometimes, in the questions, there are multiple answers just tell us what you think, feel free to use the group to ask questions.

### 1
**1.** Check out the [el-sw repository](https://github.com/fs-feup/el-sw/tree/main) code and documentation  and try to generally understand what the software does in each device (there is no need to understand all the little details).
### 2
When we read values from the brake sensor (C1) and the apps (C3) we do not use the most recent reading and use instead a different approach. Explain the approach and why you think it is used.

**Answer:** The approach consists of reading the of reading the values of the sensor, followed by inserting the values in the buffer and avaraging out the values. This method is used in order to minimize errors.


### 3
Check out the R2D(Ready To Drive) code on the C3 state machine. In the condition below we use a timer (R2DTimer) to check the brake was engaged instead of just checking the brake pressure received from can, why?
```c++
        if ((r2dButton.fell() and TSOn and R2DTimer < R2D_TIMEOUT) or R2DOverride)
        {
            playR2DSound();
            initBamocarD3();
            request_dataLOG_messages();
            R2DStatus = DRIVING;
            break;
        }
```

**Answer:** This is done so that the car can only enter R2D if the brake was engaged for enough time, increasing the safety of the car.
### 4
What is the ID of the can message sent to the bamocar to request torque?
**Answer:** 0x201
### 5 
The code below is not amazing, tell us some things you would change to improve it, you can write them down in text or correct the code:
```c++
// this is a class for my car
class mycar {
private:
    int sensor_readings[8] = {sensor_reading1, sensor_reading2, sensor_reading3, sensor_reading4,
                          sensor_reading5, sensor_reading6, sensor_reading7, sensor_reading8};

public:
    mycar() {}

    // Method will update readings by analog reading and print them 
    void updateprint() {

        for(int i = 0; i < 8; i++){
            sensor_readings[i] = analogReads(i);
        }
        func(sensor_reading1, sensor_reading2, sensor_reading3, sensor_reading4, 
              sensor_reading5, sensor_reading6, sensor_reading7, sensor_reading8);// print the readings
    }

    // function to print the readings of the sensors
    void func(int sensor_reading1, int sensor_reading2, int sensor_reading3, int sensor_reading4, 
              int sensor_reading5, int sensor_reading6, int sensor_reading7, int sensor_reading8) {

    for (int i = 0; i < 8; i++) {
         Serial.print("Sensor Reading %d: %d\n", i + 1, sensor_reading[i]);
    }

            //all readings were serial printed
        }
    };
    ```
