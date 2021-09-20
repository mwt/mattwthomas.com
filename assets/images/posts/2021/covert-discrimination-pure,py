#%% Setup
from matplotlib import rc

rc("font", **{"family": "serif", "serif": ["Computer Modern Roman"], "size": 20})
rc("text", usetex=True)

import os
import numpy as np
import mpmath as mp
import matplotlib.pyplot as plt
from scipy.special import lambertw
from scipy import optimize

# path = os.path.expanduser(
#     "~\\Documents\\Git\\mattwthomas.com\\assets\\images\\posts\\2021\\"
# )
# os.chdir(path)


# %% covert discrimination

nn = 1000  # resolution of plot
xmin = 1
xmax = 5

x = np.linspace(xmin + 1 / nn, xmax, nn)

# Create inner loop
def alphainner(a, k):
    f1 = 1 / np.log(k)
    f2 = 1 - (2 / (1 + k ** a))
    return a - f1 / f2

# pure strategy requirement
def alphabar(dk):
    logdk = np.log(dk)
    W = lambertw(-dk * logdk)
    return np.real(1 - W / logdk)

# tullock revenue
def tullock_revenue(k,r):
    return (1 + (1/k)) * (r*(k**r)) / ((k**r + 1)**2)

# apa revenue
def apa_revenue(k):
    return (1 + k) / (2 * (k**2))

# true max
def bound(k):
    return (k < 2)*(1/k) + (k >= 2)*(1/2)


# make an initial guess
f10 = 1 / np.log(x)
f20 = 1 - (2 / (1 + x))

y = optimize.root(alphainner, x0=(f10 / f20), args=(x))

# optimal r is min of two constraints
ropt = np.min([y.x,alphabar(1 / x)],0)

figure = plt.figure()
plt.plot(x, bound(x))
plt.plot(x, tullock_revenue(x, ropt))
plt.plot(x, apa_revenue(x))
plt.plot(x, tullock_revenue(x, 1))
plt.axis([xmin, xmax, 0, 1])
plt.ylabel(r"$s_1 + s_2$")
plt.xlabel(r"$k$")
plt.xticks(np.linspace(1, xmax, xmax))
plt.yticks([0,0.5,1])
plt.legend(["Optimal", "Optimal Tullock", "APA", "Tullock"])
figure.set_dpi(100)
figure.set_size_inches(4, 2.5)
figure.savefig("pure-covert-discrimination.svg", bbox_inches="tight")


# %%
