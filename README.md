# Weighetd Essentially Non-Oscillatory (WENO)
This is a Java library for one dimensional Weighted Essentially Non Oscillatory (WENO) reconstruction of arbitrary order.

You can use the library by passing the average-values and order-of-ENO-stencils as arguments.

    ReconstructedValues values = new WENO().getWenoReconstructedValues(averageValues, k);

### Example for 5th order WENO method (k=3):
    int k = 3; // Order of ENO = 3 = 5th order WENO
    int numNeigh = k - 1; // number of neighbours on each side
    // populate the average values from neighbourhood
    double[] averageValues = new double[2 * k - 1];
    for (int j = -numNeigh; j <= numNeigh; j++) {
        averageValues[j + numNeigh] = u[i + j];
    }
    // Get the reconstructed values:
    ReconstructedValues values = new WENO().getWenoReconstructedValues(averageValues, k);
    // Read the values from ReconstructedValues object
    u_imh = values.value_imh; // u at i-1/2
    u_iph = values.value_iph; // u at i+1/2

### Example for 9th order WENO method (Same code as above with k=5):
    int k = 5; // Order of ENO = 5 = 9th order WENO
    int numNeigh = k - 1; // number of neighbours on each side
    // populate the average values from neighbourhood
    double[] averageValues = new double[2 * k - 1];
    for (int j = -numNeigh; j <= numNeigh; j++) {
        averageValues[j + numNeigh] = u[i + j];
    }
    // Get the reconstructed values:
    ReconstructedValues values = new WENO().getWenoReconstructedValues(averageValues, k);
    // Read the values from ReconstructedValues object
    u_imh = values.value_imh; // u at i-1/2
    u_iph = values.value_iph; // u at i+1/2
