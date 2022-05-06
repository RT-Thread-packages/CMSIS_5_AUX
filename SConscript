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

if GetDepend('PKG_CMSIS_DSP'):
    CPPPATH = CPPPATH + [cmsis_path + 'DSP/Include']
    CPPPATH = CPPPATH + [cmsis_path + 'DSP/Include/dsp']

    dsp_BasicMathFunctions_src = Glob(cmsis_path + 'DSP/Source/BasicMathFunctions/*.c')
    dsp_BayesFunctions_src = Glob(cmsis_path + 'DSP/Source/BayesFunctions/*.c')
    dsp_CommonTables_src = Glob(cmsis_path + 'DSP/Source/CommonTables/*.c')
    dsp_ComplexMathFunctions_src = Glob(cmsis_path + 'DSP/Source/ComplexMathFunctions/*.c')
    dsp_ControllerFunctions_src = Glob(cmsis_path + 'DSP/Source/ControllerFunctions/*.c')
    dsp_DistanceFunctions_src = Glob(cmsis_path + 'DSP/Source/DistanceFunctions/*.c')
    dsp_FastMathFunctions_src = Glob(cmsis_path + 'DSP/Source/FastMathFunctions/*.c')
    dsp_FilteringFunctions_src = Glob(cmsis_path + 'DSP/Source/FilteringFunctions/*.c')
    dsp_InterpolationFunctions_src = Glob(cmsis_path + 'DSP/Source/InterpolationFunctions/*.c')
    dsp_MatrixFunctions_src = Glob(cmsis_path + 'DSP/Source/MatrixFunctions/*.c')
    dsp_QuaternionMathFunctions_src = Glob(cmsis_path + 'DSP/Source/QuaternionMathFunctions/*.c')
    dsp_StatisticsFunctions_src = Glob(cmsis_path + 'DSP/Source/StatisticsFunctions/*.c')
    dsp_SupportFunctions_src = Glob(cmsis_path + 'DSP/Source/SupportFunctions/*.c')
    dsp_SVMFunctions_src = Glob(cmsis_path + 'DSP/Source/SVMFunctions/*.c')
    dsp_TransformFunctions_src = Glob(cmsis_path + 'DSP/Source/TransformFunctions/*.c')

    if GetDepend('PKG_CMSIS_DSP_BasicMathFunctions'):
        src += dsp_BasicMathFunctions_src
    if GetDepend('PKG_CMSIS_DSP_BayesFunctions'):
        src += dsp_BayesFunctions_src
    if GetDepend('PKG_CMSIS_DSP_CommonTables'):
        src += dsp_CommonTables_src
    if GetDepend('PKG_CMSIS_DSP_ComplexMathFunctions'):
        src += dsp_ComplexMathFunctions_src
    if GetDepend('PKG_CMSIS_DSP_ControllerFunctions'):
        src += dsp_ControllerFunctions_src
    if GetDepend('PKG_CMSIS_DSP_DistanceFunctions'):
        src += dsp_ControllerFunctions_src
    if GetDepend('PKG_CMSIS_DSP_FastMathFunctions'):
        src += dsp_FastMathFunctions_src
    if GetDepend('PKG_CMSIS_DSP_FilteringFunctions'):
        src += dsp_FilteringFunctions_src
    if GetDepend('PKG_CMSIS_DSP_InterpolationFunctions'):
        src += dsp_InterpolationFunctions_src
    if GetDepend('PKG_CMSIS_DSP_MatrixFunctions'):
        src += dsp_MatrixFunctions_src
    if GetDepend('PKG_CMSIS_DSP_QuaternionMathFunctions'):
        src += dsp_QuaternionMathFunctions_src
    if GetDepend('PKG_CMSIS_DSP_StatisticsFunctions'):
        src += dsp_StatisticsFunctions_src
    if GetDepend('PKG_CMSIS_DSP_SupportFunctions'):
        src += dsp_SupportFunctions_src
    if GetDepend('PKG_CMSIS_DSP_SVMFunctions'):
        src += dsp_SVMFunctions_src
    if GetDepend('PKG_CMSIS_DSP_TransformFunctions'):
        src += dsp_TransformFunctions_src


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
