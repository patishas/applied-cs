# applied-cs
Selection of projects from CS 74 Machine Learning and CS 70 Linear Algebra

## CS 70 Linear Algebra Labs

### Photo Compositing

Code that seamlessly blends a source image into a target image using Poisson blending, works similarly to the blending tools in Adobe Photoshop

The significance of this is that it blends in all 2 dimensions, creating a gradual transition from the source image to the target image in all directions.
If we had blended in 1D, there would've been 2 visible borders of the source image, and if we hadn't blended at all (think a simple copy-paste), all 4 borders of the source image would've been visible. The beauty of this code is that it can be applied to any 2 images whose backgrounds are relatively similar and uniform.

A gallery of images generated by this code is viewable in this repository and on my website.

#### Usage

A user can load their own images into im_object and im_background as shown below:

```
im_object = plt.imread('images/your_object.jpg')/255.0
im_background = plt.imread('images/your_background.jpg')/255.0
```
Then call `onclick()` to select where on the background image the source should be inserted. Then call `poisson_copy_paste()` to blend.
The image will be saved under the title passed into `plt.imsave()`

#### Assumptions

The backgrounds of the source and target images are relatively similar in color. If the colors differs too much, the source image will be tinted.
Also assumes the background will be uniform. If either background contains too much detail, this detail may be lost after blending.

### Inverse Kinematics using Newton's Method

Code that calculates joint angles, allowing a jointed limb (eg. a jointed robotic arm) to reach a target location in 2D space

Significant in the field of computer animation. Manually manipulating joints (think shoulders, elbows, knees) by hand can be incredibly tedious: all of the parameters are interdependent and must be adjusted in a coordinated manner.
To get around this, inverse kinematics techniques apply numerical root finding to determine solutions to this problem in an automated way. In fact, most modern animation systems implement inverse kinematics solutions like this since it allows for a much more convenient workflow: rather than having to tweak each individual bone, artists can directly specify a target shape, and the system will automatically infer all the necessary rotations.

#### Usage

A user can call `fkdemo()` and use the sliders to achieve a manual forward kinematics solution.
Alternatively, a user can call `ikdemo()` to test the inverse kinematics solver and automatically generate a solution.


### Monte Carlo Modeling

Code that performs a Monte Carlo simulation and analyzes its rate of convergence. This method relies on repeated random sampling to obtain numerical results.

Significant to 3D computer graphics, particularly ray tracing and light modeling. Think: What contributes to the RGB value of a particular point in a room? It is not just the color of the point itself that's important, but the colors reflecting onto it from nearby walls and objects and the color of the light source as well. To further the complexity, the colors in the room are interdependent. Each point contributes to the color of other points in the room, as adjusting the RGB of point A may change the RGB reflected onto points B and C. Thus, calculating accurate RGBs for every point in the room becomes exponentially difficult.
Monte Carlo settles for an approximation of these RGB values with the benefit of increased efficiency. It is efficient enough that it allows for realtime ray tracing and light modeling in video games like *Battlefield 5* and *Witcher 3*. With increased iterations, it can be also used to generate photorealistic images for film, as done for Alfonso Cuarón's *Gravity*.



## CS 74 Machine Learning Labs

### Least Squares Linear Regression and Gradient Descent

Trains a linear regression model using least squares cost and gradient descent (a type of learning algorithm) on an 80-20 train-test split. Tests using MSE (mean squared error).
Done both manually and using the sklearn library.

### Logistic Regression Cross Entropy Cost

Trains a logistic regression model (for classification) using cross entropy cost and gradient descent on an 80-20 train-test split. Evaluates model using an ROC curve.
Done both manually and using the sklearn library.
