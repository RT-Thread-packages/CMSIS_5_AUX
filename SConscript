import os
from building import *

group      = []
cwd        = GetCurrentDir()
src        = []
CPPPATH    = []
CPPDEFINES = []

packages_root_path = cwd + '/../'

def find_CMSIS_5_folder(root_path):
    dirs = os.listdir(root_path)
    for dir in dirs:
        if os.path.isdir(packages_root_path + dir):
            if "CMSIS_5-" in dir:
                return dir
    print("Cannot find CMSIS_5's path!")
    return None

cmsis_folder_name = find_CMSIS_5_folder(packages_root_path)
if (cmsis_folder_name == None):
    Return('group') # if we cannot find the CMSIS folder, it will directly return

cmsis_path = packages_root_path + cmsis_folder_name + '/CMSIS/'

if GetDepend('PKG_CMSIS_CORE'):
    CPPPATH += [cmsis_path + 'Core/Include']

if GetDepend('PKG_CMSIS_DSP'):
    CPPPATH += [cmsis_path + 'DSP/Include']
    CPPPATH += [cmsis_path + 'DSP/Include/dsp']
    CPPPATH += [cmsis_path + 'DSP/PrivateInclude']

    if GetDepend('PKG_CMSIS_DSP_BASIC_MATH'):
        src += Glob(cmsis_path + 'DSP/Source/BasicMathFunctions/*.c')
    if GetDepend('PKG_CMSIS_DSP_BAYES'):
        src += Glob(cmsis_path + 'DSP/Source/BayesFunctions/*.c')
    if GetDepend('PKG_CMSIS_DSP_COMMON_TABLES'):
        src += Glob(cmsis_path + 'DSP/Source/CommonTables/*.c')
    if GetDepend('PKG_CMSIS_DSP_COMPLEX_MATH'):
        src += Glob(cmsis_path + 'DSP/Source/ComplexMathFunctions/*.c')
    if GetDepend('PKG_CMSIS_DSP_CONTROLLER'):
        src += Glob(cmsis_path + 'DSP/Source/ControllerFunctions/*.c')
    if GetDepend('PKG_CMSIS_DSP_DISTANCE'):
        src += Glob(cmsis_path + 'DSP/Source/DistanceFunctions/*.c')
    if GetDepend('PKG_CMSIS_DSP_FAST_MATH'):
        src += Glob(cmsis_path + 'DSP/Source/FastMathFunctions/*.c')
    if GetDepend('PKG_CMSIS_DSP_FILTERING'):
        src += Glob(cmsis_path + 'DSP/Source/FilteringFunctions/*.c')
    if GetDepend('PKG_CMSIS_DSP_INTERPOLATION'):
        src += Glob(cmsis_path + 'DSP/Source/InterpolationFunctions/*.c')
    if GetDepend('PKG_CMSIS_DSP_MATRIX'):
        src += Glob(cmsis_path + 'DSP/Source/MatrixFunctions/*.c')
    if GetDepend('PKG_CMSIS_DSP_QUATERNION_MATH'):
        src += Glob(cmsis_path + 'DSP/Source/QuaternionMathFunctions/*.c')
    if GetDepend('PKG_CMSIS_DSP_SVM'):
        src += Glob(cmsis_path + 'DSP/Source/SVMFunctions/*.c')
    if GetDepend('PKG_CMSIS_DSP_STATISTICS'):
        src += Glob(cmsis_path + 'DSP/Source/StatisticsFunctions/*.c')
    if GetDepend('PKG_CMSIS_DSP_SUPPORT'):
        src += Glob(cmsis_path + 'DSP/Source/SupportFunctions/*.c')
    if GetDepend('PKG_CMSIS_DSP_TRANSFORM'):
        src += Glob(cmsis_path + 'DSP/Source/TransformFunctions/*.c')

if GetDepend('PKG_CMSIS_NN'):
    CPPPATH += [cmsis_path + 'NN/Include']

    if GetDepend('PKG_CMSIS_NN_ACTIVATION'):
        src += Glob(cmsis_path + 'NN/Source/ActivationFunctions/*.c')
    if GetDepend('PKG_CMSIS_NN_BASIC_MATH'):
        src += Glob(cmsis_path + 'NN/Source/BasicMathFunctions/*.c')
    if GetDepend('PKG_CMSIS_NN_CONCATENATION'):
        src += Glob(cmsis_path + 'NN/Source/ConcatenationFunctions/*.c')
    if GetDepend('PKG_CMSIS_NN_CONVOLUTION'):
        src += Glob(cmsis_path + 'NN/Source/ConvolutionFunctions/*.c')
    if GetDepend('PKG_CMSIS_NN_FULLY_CONNECTED'):
        src += Glob(cmsis_path + 'NN/Source/FullyConnectedFunctions/*.c')
    if GetDepend('PKG_CMSIS_NN_SUPPORT'):
        src += Glob(cmsis_path + 'NN/Source/NNSupportFunctions/*.c')
    if GetDepend('PKG_CMSIS_NN_POOLING'):
        src += Glob(cmsis_path + 'NN/Source/PoolingFunctions/*.c')
    if GetDepend('PKG_CMSIS_NN_RESHAPE'):
        src += Glob(cmsis_path + 'NN/Source/ReshapeFunctions/*.c')
    if GetDepend('PKG_CMSIS_NN_SVDF'):
        src += Glob(cmsis_path + 'NN/Source/SVDFunctions/*.c')
    if GetDepend('PKG_CMSIS_NN_SOFTMAX'):
        src += Glob(cmsis_path + 'NN/Source/SoftmaxFunctions/*.c')

if GetDepend('PKG_USING_CMSIS_RTOS2'):
    CPPPATH += [cmsis_path + 'RTOS2/Include']

if GetDepend('PKG_CMSIS_RTOS2_COMPATIBLE_CMSIS_RTOS1'):
    CPPPATH = CPPPATH + [cmsis_path + 'RTOS2/Template']
    src += Glob(cmsis_path + 'RTOS2/Template/*.c')

# Definitions for MATH
if GetDepend('ARCH_ARM_CORTEX_M7'):
    CPPDEFINES += ['ARM_MATH_CM7']
elif GetDepend('ARCH_ARM_CORTEX_M4'):
    CPPDEFINES += ['ARM_MATH_CM4']
elif GetDepend('ARCH_ARM_CORTEX_M3'):
    CPPDEFINES += ['ARM_MATH_CM3']
elif GetDepend('ARCH_ARM_CORTEX_M4'):
    CPPDEFINES += ['ARM_MATH_CM4']
elif GetDepend('ARCH_ARM_CORTEX_M0'):
    CPPDEFINES += ['ARM_MATH_CM0']

if GetDepend('ARCH_ARM_CORTEX_FPU'):
    CPPDEFINES += ['__FPU_PRESENT=1']

group = DefineGroup('CMSIS-5', src, depend = ['PKG_USING_CMSIS_5'], CPPPATH = CPPPATH, LOCAL_CPPDEFINES=CPPDEFINES)

Return('group')
