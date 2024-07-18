# Building OpenRAVE on Ubuntu 22.04 with Python 3.10

## Prerequisites
Environment:
- Ubuntu 22.04
- Python 3.10

## Issues and Fixes (written on 10/7/2024)

### 1. FCL Build Error

**Error**: `octree dont have .getChild`

**Cause**: The `getChild(...)` function was moved to `OcTreeBaseImpl::getNodeChild(...)` since [v1.8.0](https://github.com/OctoMap/octomap/releases/tag/v1.8.0).

**Fix**: Build OctoMap from source, using a version earlier than 1.8.0 (version used: v1.6.8).

**Additional Issue**: `reference to ‘byte’ is ambiguous`

**Fix**: Remove `using namespace std;` and prefix required items with `std::`.

### 2. OpenRAVE Build Error

**Error**: `'shared_mutex’ in namespace ‘std’ does not name a type`

**Cause**: `shared_mutex` requires C++17.

**Fix**: Update the code to use `boost::shared_mutex`. Reference [this issue](https://github.com/acxz/pkgbuilds/issues/148) for details.

### 3. Nose Error

**Error**: `AttributeError 'collections' has no attribute 'Callable'`

**Cause**: In Python 3.10, `collections.Callable` has been replaced with `collections.abc.Callable`.

**Fix**: Update the code to use `collections.abc.Callable`. Refer to [this issue](https://github.com/nose-devs/nose/issues/1122) for more information.

