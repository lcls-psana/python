#--------------------------------------------------------------------------
# File and Version Information:
#  $Id$
#
# Description:
#  SConscript file for package python
#------------------------------------------------------------------------

# Do not delete following line, it must be present in 
# SConscript file for any SIT project
Import('*')

from SConsTools.standardExternalPackage import standardExternalPackage
import os, glob

#
# For the standard external packages which contain includes, libraries, 
# and applications it is usually sufficient to call standardExternalPackage()
# giving some or all parameters.
#

# Python configuration is determined by SConsTools, check SCons tools psdm_python

assert env.get('CONDA', False), "not conda build"

python = env['PYTHON']   # python with version number such as python2.7
PREFIX = env['PYTHON_PREFIX']
INCDIR = env['PYTHON_INCDIR']
LIBDIR  = env['PYTHON_LIBDIR']
BINDIR  = env['PYTHON_BINDIR']
PKGLIBS = python
# Handle python libraries with extra 'm'. Python 3.8 and beyond dropped this
if glob.glob(os.path.join(LIBDIR, "lib"+python+".so*")):
  LINKLIBS = ["lib"+python+".so*", 'libtcl.so*', 'libtk.so*']
else:
  LINKLIBS = ["lib"+python+"m.so*", 'libtcl.so*', 'libtk.so*']
LINKBINS = ["python", python]

standardExternalPackage('python', **locals())
