Import('RTT_ROOT')
from building import *

# get current directory
cwd = GetCurrentDir()

# The set of source files associated with this SConscript file.
src = Glob('common/*.c')
src += Glob('libhttp/*.c')
src += Glob('httpclient/*.c')
src += Glob('network/*.c')
src += Glob('platform/RT-Thread/*.c')

path = [cwd + '/common']
path += [cwd + '/libhttp']
path += [cwd + '/httpclient']
path += [cwd + '/network']
path += [cwd + '/platform/RT-Thread']

if GetDepend(['KAWAII_HTTP_NETWORK_TYPE_TLS']):
    src += Glob('network/mbedtls/library/*.c')
    src += Glob('network/mbedtls/wrapper/*.c')
    path += [cwd + '/network/mbedtls/wrapper']
    path += [cwd + '/network/mbedtls/include']
    path += [cwd + '/network/mbedtls/include/mbedtls']

if GetDepend(['KAWAII_HTTP_LOG_IS_SALOF']):
    src += Glob('common/log/*.c')
    path += [cwd + '/common/log']
    
if GetDepend(['PKG_USING_KAWAII_HTTP_TEST']):
    src += Glob('test/*.c')

group = DefineGroup('kawaii_http',src , depend = ['PKG_USING_KAWAII_HTTP'], CPPPATH = path)

Return('group')
