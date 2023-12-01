# OSSW_final_project

**Final project of the course 'Open Source Software', making my own machine learning algorithm.**

_What has been done_

The first problem of this task was to figure out what kind of model supported by the scikit learn package I wanted to use. After some research, I found that SVC and random forest were the most suited for my purpose. I then did some experiments with both of them and found that the SVC yielded better results 'out of the box'. I then went on to fine tune the model's hyperparameters using GridSearchCV, which finds the best parameters from a set. The performance flattened at around 92%, so I settled with this.

_The training data set_

The training data set is a folder containging MRI scans of brains. The scans depicts three different categories of brain tumors; glioma, meningioma and pitiuray, and finally a scans of healthy brains. In total, this gives four different categories to train on.

_My algorithm_

Support vector machines (SVC) have good utility for classifying pictures. This is becuase it aims to find a hyperplane that best classifies different data points in a high-dimensional space. For SVCs, the hyperplane is the decision boundary and is defined as the line that maximizes the margin between the classes. The marigin is the distance between the hyperplane and the closest point from each class. These points are called support vectors.

_Hyperparameters_

class sklearn.svm.SVC(\*, C=1.0, kernel='rbf', degree=3, gamma='scale', coef0=0.0, shrinking=True, probability=False, tol=0.001, cache_size=200, class_weight=None, verbose=False, max_iter=-1, decision_function_shape='ovr', break_ties=False, random_state=None)

**C** = Regularization parameters associated with the soft boundary\n
**kernel** = What kernel is used to transform the input featuers into higher dimentional space\n
**degree** = Degree of polynomial if kernel = 'poly'\n
**gamma** = kernel coefficient for kernel = 'poly', 'rbf' or 'sigmoid'\n
**coef0** = The indendent term in kernel function for 'poly' and 'sigmoid'\n
**shrinking** = Decides whether to use shrinking function\n
**probability** = Decides whether to enable probability estimates\n
**tol** = The tolerance for stopping\n
**cache_size** = Size of kernel cache\n
**class_weight** = Enables to weight the classes differently\n
**verbose** = Enables verbose output\n
**max_iter** = Limit on iterations for solver\n
**decision_function_shape** = Decides the shape of the returned decision function\n
**break_ties** = Decides if _predict_ will break ties according to confidence values of _decision_function_\n
**random_state** = Controls the pseudo random number generation for shuffling the data for probability estimates\n
