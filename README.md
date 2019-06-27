# deep_vehicle_following_training
Use fish camera to following car

How to use the file
1. run joystick_camera.launch or any launch which has the car_cmd_switch_node/cmd and camera_node/image/compressed topic on duckiebot
2. use rosbag record command to record one or more bag files which only subscribe the two topics mentioned in 1. (recommend: use "--split --size 2048" parameter to split bag into multiple 2G bag files, cause the bag will corrupt if the size is too large)
3. use bag2txt.py to draw out the image and omega value. For more info, see bag2txt.py
4. put the folder with images into 'images' under 'for_ncs', and move the train.txt & test.txt to 'splits' folder under 'for_ncs'
5. after setup the environment, run 'python train.py' to start the training, more info in the train.py
6. after the training is done, there'll be a file called solvertemplate_iter_100000.caffemodel under for_ncs/results/0/snapshots/
7. If you want to deploy the result to ncs, the rest process is the same as we taught in this summer school
