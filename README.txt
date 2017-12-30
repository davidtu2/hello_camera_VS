David Tu
david.tu2@csu.fullerton.edu

A program which draws a teapot with two light sources, based on Professor Shafae's hello_glsl program.
This program adds additional controls which evokes the following functions:
    O button: moveCameraForward
	L button: moveCameraBackward
	K button: panCameraLeft
	; button: panCameraRight
The reset button has also been updated due to the additional functionality mentioned.

The following will describe the additional functionality:
1. moveCameraForward: As the name implies, this will move the camera forward. To implement this function, I had to find out the direction the camera was going every time the a button was pressed. To get this direction, I subtracted the centerPostion and the eyePosition and normalized the result. This will always give me the vector that the camera is facing which I called "g". Then I multiplied g by the amount that I want the camera to move. In this implementation, I made the camera move by 0.05. The resulting product is added to the eyePosition and centerPosition which moves the camera forward.

2. moveCameraBackward: This function will make the camera move backwards. It is acctually the same implementation as moveCameraForward but instead of adding I have used subtraction.

3. panCameraLeft: This function will have the camera turn left from it's position. To implement this function, I first need to find out what the camera is looking at. To get this vector which I will call "g", I subtracted the centerPosition with the eyePosition. I then created a rotation matrix called rotationMatrix to multiply with g. This will make g rotated into some direction. I then took g and decomposed it into it's parts:
	g = c - e where 
	c = the position that g is pointing and 
	e = the camera position
Then solve for c:
	c = g + e
Once c is determined, I then update the centerPosition with c.

4. panCameraRight: This function will have the camera turn right from it's position. The implementation of this function is the same as the panCameraLeft function except the rotation matrix is modified to turn clockwise instead of counter-clockwise by negating the variable, rotationDelta.
