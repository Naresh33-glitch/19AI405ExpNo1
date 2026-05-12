# ExpNo 1 :Developing AI Agent with PEAS Description
## Name: NARESH S
## Register Number: 212224240101
# AIM:

To find the PEAS description for the given AI problem and develop an AI agent.


# Theory:
## Medicine prescribing agent:
Such this agent prescribes medicine for fever (greater than 98.5 degrees) which we consider here as unhealthy, by the user temperature input, and another environment is rooms in the hospital (two rooms). This agent has to consider two factors one is room location and an unhealthy patient in a random room, the agent has to move from one room to another to check and treat the unhealthy person. The performance of the agent is calculated by incrementing performance and each time after treating in one room again it has to check another room so that the movement causes the agent to reduce its performance. Hence, agents prescribe medicine to unhealthy.

## PEAS DESCRIPTION:
Agent Type	Performance	Environment	Actuators	Sensors
Medicine prescribing agent	Treating unhealthy, agent movement	Rooms, Patient	Medicine, Treatment	Location, Temperature of patient
## DESIGN STEPS:
STEP 1:Identifying the input:
Temperature from patients, Location.

STEP 2:Identifying the output:
Prescribe medicine if the patient in a random has a fever.

STEP 3:Developing the PEAS description:
PEAS description is developed by the performance, environment, actuators, and sensors in an agent.

STEP 4:Implementing the AI agent:
Treat unhealthy patients in each room. And check for the unhealthy patients in random room

STEP 5:
Measure the performance parameters: For each treatment performance incremented, for each movement performance decremented

# PROGRAM:
~~~py
import random

class MedicineAgent:
    def __init__(self):
        self.location = "Room A"
        self.performance = 0

    def act(self, environment):
        temp = environment[self.location]["temperature"]
        
        if temp > 98.5:
            print(f"Patient in {self.location} unhealthy ({temp:.1f}°F). Giving medicine.")
            self.performance += 10
            environment[self.location]["temperature"] = 98.0
        else:
            print(f"Patient in {self.location} healthy ({temp:.1f}°F).")

        self.location = "Room B" if self.location == "Room A" else "Room A"
        self.performance -= 1
        print(f"Moving to {self.location}. Performance: {self.performance}")
        print("-" * 30)

def main():
    environment = {
        "Room A": {"temperature": random.uniform(97.0, 102.0)},
        "Room B": {"temperature": random.uniform(97.0, 102.0)}
    }
    agent = MedicineAgent()

    print("Starting simulation.")
    print("-" * 30)

    for step in range(5):
        print(f"--- Step {step + 1} ---")
        agent.act(environment)
        
        random_room = random.choice(["Room A", "Room B"])
        environment[random_room]["temperature"] = random.uniform(99.0, 103.0)

    print("Simulation finished.")

if __name__ == "__main__":
    main()
~~~
# OUTPUT:
<img width="420" height="356" alt="553319760-e2e016ab-7ca6-4050-b5a7-95a1e7b2d1c3" src="https://github.com/user-attachments/assets/2948e59f-b8f8-4652-ae88-b222bc5813b2" />


# RESULT:
Thus th PEAS description for the given AI problem and develop an AI agent is implemented successfully.
