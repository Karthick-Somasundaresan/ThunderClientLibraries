# If not stated otherwise in this file or this component's license file the
# following copyright and licenses apply:
#
# Copyright 2020 Metrological
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
# http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

set(TARGET implementation)

#find_package(OpenSSL REQUIRED)

add_library(${TARGET} STATIC
    Vault.cpp
    Hash.cpp
    Cipher.cpp
    #Derive.cpp
    DiffieHellman.cpp
    VaultNetflix.cpp
    HashTypeNetflix.cpp
    CipherNetflix.cpp

)

target_link_libraries(${TARGET}
    PUBLIC
        ${NAMESPACE}Core::${NAMESPACE}Core
	-lsec_api
	-lsec_api_netflix
)
#OpenSSL::SSL
#        OpenSSL::Crypto

target_include_directories(${TARGET}
    PUBLIC
        $<BUILD_INTERFACE:${CMAKE_CURRENT_LIST_DIR}/../>
        $<BUILD_INTERFACE:${CMAKE_CURRENT_LIST_DIR}/../..>)
