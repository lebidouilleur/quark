# meson.build ---                                            -*- mode: meson; -*-
#
# Copyright (C) 2021  lebidouilleur
#
# Author: lebidouilleur <lebidouilleur@icloud.com>
# Keywords:
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#
# Code:
#




# Define the project with a project name, a version, a license, a programming
# language, a minimum `meson` version and some default options.
# `meson` will create following variables for you:
#   - meson.project_name()
#   - meson.project_license()
#   - meson.project_version()
#
#   - meson.version()
# NOTE: There will ALWAYS be someone using a previous version of `meson'.
#       Be sure to select an old enough one to prevent compilation issue.
project(                 'quark',
                         'c',
                license: 'GPL3+',
                version: '0.0.1',
          meson_version: '>= 0.55.0',
        default_options: [ 'c_std=c17',         'cpp_std=c++17',
                           'buildtype=minsize', 'optimization=2',
                           'warning_level=3' ] )




# Since it's imposssible to define this variable before the project macro,
# we redefine here the programming language used in the project.
# Take a look at
# https://mesonbuild.com/Reference-tables.html#language-arguments-parameter-names
# to find any other accepted language.
# Default: [ 'c' ]
LANGUAGE = 'c'




# The GNU Coding Standards define a standard way to install projects on a
# GNU system.  It has become a de facto standard for almost every open source
# projects.
subdir('meson/GNUStandardDirs')




# Setup the compiler with the given `LANGUAGE` and add compiler flags.
# Be aware that compiler flags are specific to a certain buildtypes.
cc = meson.get_compiler(LANGUAGE)
subdir('meson/CompileFlags')




# Create a list of your files for further reuse in subdirectories.
# NOTE: Do not forget to add `main.[c,cpp,...]` for avoid errors.
sources  = [ 'main.c' ]
includes = include_directories('include')




# Append files to `sources` through `meson.build` in `source` subdirectory.
subdir('source')




# Define the executable target.
executable(meson.project_name(), sources: sources,
                                 include_directories: includes,
                                 install: true)

install_data(
  sources: [ 'LICENSE', 'README.md' ],
  install_dir : join_paths(datadir, meson.project_name()))
