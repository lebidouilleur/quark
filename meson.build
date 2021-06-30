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



project(                 'QUARK',
                         'c',
                license: 'GPL3+',
                version: '0.0.1',
          meson_version: '>= 0.55.0',
        default_options: [ 'c_std=c17', 'cpp_std=c++17',
                           'warning_level=3' ])




prefix     = get_option('prefix')
bindir     = join_paths(prefix, get_option('bindir'))
libdir     = join_paths(prefix, get_option('libdir'))
mandir     = join_paths(prefix, get_option('mandir'))
datadir    = join_paths(prefix, get_option('datadir'))
localedir  = get_option('localedir')






# Setup the compiler
cc = meson.get_compiler('c')
if  get_option('buildtype') == 'release'
  compile_flags = [ '-march=native', '-mtune=native', '-pipe' ]

  supported_flags = cc.get_supported_arguments(compile_flags)
  add_project_arguments(supported_flags, language: 'c')
else
  if get_option('buildtype').startswith('debug')
    # Add compilation flags
    compile_flags = [ '-W',                   '-Wcast-align',
                      '-Wcast-qual',          '-Wconversion',
                      '-Werror',              '-Wmissing-declarations',
                      '-Wmissing-prototypes', '-Wnested-externs',
                      '-Wpointer-arith',      '-Wshadow',
                      '-Wstrict-prototypes',  '-Wunused',
                      '-Wunused-function',    '-Wunused-label',
                      '-Wunused-macros',      '-Wunused-parameter',
                      '-Wunused-value',       '-Wunused-variable',
                      '-Wwrite-strings',      '-g' ]

    supported_flags = cc.get_supported_arguments(compile_flags)
    add_project_arguments(supported_flags, language: 'c')
  endif
endif

includeDir = include_directories('include')

executable('quark', 'main.c', include_directories: includeDir,
                              install: true)
