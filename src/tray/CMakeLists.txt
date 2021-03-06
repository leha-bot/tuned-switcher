#
# SPDX-FileCopyrightText: 2021 EasyCoding Team and contributors
#
# SPDX-License-Identifier: GPL-3.0-or-later
#

set(CMAKE_AUTOMOC ON)

set(SOURCES
    trayicon/trayicon.cpp
    main.cpp
)

set(HEADERS
    trayicon/trayicon.h
)

qt5_add_resources(RESOURCES
    resources.qrc
)

set(INTERNAL_LIBS
    ${SOURCES}
    ${HEADERS}
    ${MOC_HEADERS}
    ${RESOURCES}
)

set(EXTERNAL_LIBS
    Qt5::Widgets
    Qt5::DBus
    tuned-switcher-lib
)

add_executable(${APPLET_NAME} ${INTERNAL_LIBS})
target_link_libraries(${APPLET_NAME} PRIVATE ${EXTERNAL_LIBS})

install(TARGETS ${APPLET_NAME} RUNTIME DESTINATION "${CMAKE_INSTALL_BINDIR}" BUNDLE DESTINATION "${CMAKE_INSTALL_BINDIR}")
