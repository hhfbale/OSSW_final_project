# OSSW_final_project

_Final project of the course 'Open Source Software', making my own machine learning algorithm._

## What has been done

The first problem of this task was to figure out what kind of model supported by the scikit learn package I wanted to use. After some research, I found that support vector classification (SVC) and Random Forest Classification were the most suited for my purpose. I did experimentation with both of them and found that the SVC yielded better results 'out of the box'. I then went on to fine tune the model's hyperparameters using GridSearchCV, which finds the best parameters from a set of pre-defined parameters. The performance flattened at around 92%.

## The training data set

The training data set is a folder contaning MRI scans of brains. The scans depicts three different categories of brain tumors; glioma, meningioma and pitiuray, and finally some scans of healthy brains. In total, this gives four different categories to train on and to classify.

## My algorithm

Support vector classification (SVC) have good utility for classifying pictures. This is becuase it aims to find a hyperplane that best classifies different data points in a high-dimensional space. For SVCs, the hyperplane is the decision boundary and is defined as the line that maximizes the margin between the classes. The marigin is the distance between the hyperplane and the closest point from each class. These points are called support vectors. Since the feature points are in a high dimentioal space, the computation would be quite complex, especially if the decision boundaries are non-linear. This is where the kernel trick comes in. By Mercer's theorem, we can compute the dot product of the transformed feauture vectors in its higher dimentional space implicitly. Another important aspect of the SVC is the soft margins, whihch allows for missclassification where definite boundaries does not exist as a result of e.g. noise. This soft boundary is a trade off between missclassification and a wide marigin and is controlled by the parameter $C$, which you will see me modify in my model. Once the hyperplane is decided, new data points are classified by evaluationg on which side of the plane they fall.

## Hyperparameters

_SVC class:_
class sklearn.svm.SVC(C=1.0, kernel='rbf', degree=3, gamma='scale', coef0=0.0, shrinking=True, probability=False, tol=0.001, cache_size=200, class_weight=None, verbose=False, max_iter=-1, decision_function_shape='ovr', break_ties=False, random_state=None)

_My model:_
svm_clf = sklearn.svm.SVC(C = 50, gamma=0.011)

**C** = Regularization parameters associated with the soft boundary. I found best results when increasing C, which results in low tolerance of missclassifications.

**kernel** = What kernel is used to transform the input featuers into higher dimentional space. I had good results with the default Radial Basis Function $K(x,y) = exp(-\frac{\lVert x-y \rVert^2}{2\sigma^2})$, which can produce a non-linear hyperplane.

**degree** = Degree of polynomial if kernel = 'poly'

**gamma** = The gamma parameter decides how much the decision boundary is influenced by individual point. A value of 0.011 is low and results in a more smooth and may also generalize well to unseen data.

**coef0** = The indendent term in kernel function for 'poly' and 'sigmoid'

**shrinking** = Decides whether to use shrinking heuristic

**probability** = Decides whether to enable probability estimates, relevant if predict_proba is used.

**tol** = The tolerance for stopping. Experienced no major inpact when changing this.

**cache_size** = Size of kernel cache.

**class_weight** = Enables to weight the classes differently.

**verbose** = Determines whether the training process prints information about the optimization or not.

**max_iter** = Limit on iterations for solver. Unbound in my case.

**decision_function_shape** = Decides the shape of the returned decision function. The default 'ovr' means one-vs-rest, which means that a binary classifier is trained for each class against the rest of the classes. This proved the most useful in my testing.

**break_ties** = Decides if _predict_ will break a tied score according to confidence values of decision_function. Did not affect my model when changed.

**random_state** = Controls the pseudo random number generation for shuffling the data for probability estimates. Not relevant.
