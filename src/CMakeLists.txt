find_package(Icecream REQUIRED)

add_definitions (${QT_DEFINITIONS} ${KDE4_DEFINITIONS} -DQT3_SUPPORT_WARNINGS -DQT3_SUPPORT)

include_directories (${LIBICECREAM_INCLUDE_DIR} ${KDE4_INCLUDES})

set(icemon_SRCS
  job.cc
  monitor.cc
  mon-kde.cc
  hostinfo.cc
  statusview.cc
  detailedhostview.cc
  hostlistview.cc
  joblistview.cc
  listview.cc
  ganttstatusview.cc
  summaryview.cc
  starview.cc
  poolview.cc
)

kde4_add_executable(icemon ${icemon_SRCS})

target_link_libraries(icemon ${KDE4_KDEUI_LIBS} ${LIBICECREAM_LIBRARIES} ${QT_QTNETWORK_LIBRARY} ${QT_QT3SUPPORT_LIBRARY} ${CMAKE_DL_LIBS})

########### install files ###############

install(TARGETS icemon ${INSTALL_TARGETS_DEFAULT_ARGS})

install( FILES icemon.desktop DESTINATION ${XDG_APPS_INSTALL_DIR} )
install( FILES icemonui.rc DESTINATION ${DATA_INSTALL_DIR}/icemon )

kde4_install_icons( ${ICON_INSTALL_DIR}   )
