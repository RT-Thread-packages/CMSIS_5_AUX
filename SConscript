import os
from building import *

group      = []
cwd        = GetCurrentDir()
src        = []
CPPPATH    = []
CPPDEFINES = []

cmsis_folder_name = 'CMSIS_5-latest'
cmsis_path = cwd + '/../' + cmsis_folder_name + '/CMSIS/'

if GetDepend('PKG_CMSIS_CORE'):
    CPPPATH = CPPPATH + [cmsis_path + 'Core/Include']

if GetDepend('PKG_CMSIS_NN'):
    CPPPATH = CPPPATH + [cmsis_path + 'NN/Include']

    nn_activation_src = Glob(cmsis_path + 'NN/Source/ActivationFunctions/*.c')
    nn_convolution_src = Glob(cmsis_path + 'NN/Source/ConvolutionFunctions/*.c')
    nn_fully_connected_src = Glob(cmsis_path + 'NN/Source/FullyConnectedFunctions/*.c')
    nn_support_src = Glob(cmsis_path + 'NN/Source/NNSupportFunctions/*.c')
    nn_pooling_src = Glob(cmsis_path + 'NN/Source/PoolingFunctions/*.c')
    nn_softmax_src = Glob(cmsis_path + 'NN/Source/SoftmaxFunctions/*.c')

    if GetDepend('PKG_CMSIS_NN_ACTIVATION'):
        src += nn_activation_src
    if GetDepend('PKG_CMSIS_NN_CONVOLUTION'):
        src += nn_convolution_src
    if GetDepend('PKG_CMSIS_NN_FULLY_CONNECTED'):
        src += nn_fully_connected_src
    if GetDepend('PKG_CMSIS_NN_SUPPORT'):
        src += nn_support_src
    if GetDepend('PKG_CMSIS_NN_POOLING'):
        src += nn_pooling_src
    if GetDepend('PKG_CMSIS_NN_SOFTMAX'):
        src += nn_softmax_src

if GetDepend('PKG_CMSIS_RTOS2_COMPATIBLE_CMSIS_RTOS1'):
    CPPPATH = CPPPATH + [cmsis_path + 'RTOS2/Template']
    src += Glob(cmsis_path + 'RTOS2/Template/*.c')

if GetDepend('PKG_USING_CMSIS_RTOS2'):
    CPPPATH = CPPPATH + [cmsis_path + 'RTOS2/Include']

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
