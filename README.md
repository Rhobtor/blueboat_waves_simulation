FROM:https://github.com/ArduPilot/SITL_Models/blob/master/Gazebo/docs/BlueBoat.md
Gazebo and the plugins should be installed as per the ArduPilot Gazebo Plugin instructions.

Update the GZ_SIM_RESOURCE_PATH to include these models:

export GZ_SIM_RESOURCE_PATH=$GZ_SIM_RESOURCE_PATH:\
$HOME/SITL_Models/Gazebo/models:\
$HOME/SITL_Models/Gazebo/worlds

Waves model

The model is configured to work with the hydrodynamics plugin from the wave sim package. Follow the package instructions to set up the marine simulation.

The model may be included in the waves.sdf world by adding the element:

<include>
  <pose degrees="true">0 0 0 0 0 90</pose>
  <uri>model://blueboat</uri>
</include>

Run Gazebo

gz sim -v4 -r waves.sdf

Run ArduPilot SITL

sim_vehicle.py -v Rover -f rover-skid --model JSON  --console --map --custom-location='51.566151,-4.034345,10.0,-135'

The default skid steer rover parameters give a workable simulation with minor modifications:
