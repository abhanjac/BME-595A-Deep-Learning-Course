# Creating Depth image from 2D RGB image.
In this project, we focus on the task of depth estimation from a single input image RGB image. Estimating depth using stereo camera or by camera under motion has been explored before, but the need of estimating the depth from a 2D image still often arise in practice in many indoor and outdoor applications. We want to apply CNN to this task and analyze its performance.
## Team members
- Arindam Bhanja Chowdhury [GitHubUserA](https://github.com/abhanjac)
- Soumendu Kumar Ghosh [GitHubUserB](https://github.com/soumendukrg)
## Goals
* Give an RGB image as input to the network and get a depth image as output.
* Analyze different available CNN architectures and come up with a structure that can suit the required purpose.
* Compare the output of this CNN with the output of the depth cameras like the Micorsoft Kinect.
## Challenges
* Estimating depths from an single monocular image is a well-known ill-posed problem, since an RGB image may correspond to several different kinds of real world scenes and no reliable visual cues can be obtained for calculting the depth.
* The mapping between a single image and the depth map is inherently ambiguous, and requires both global and local information.
