qt4_wrap_cpp(MOC_SRCS
  add_feed_dialog.h
  article_list_model.h
  article_list_page.h
  article_page.h
  feed_fetcher.h
  feed_list_model.h
  feeds_page.h
  main_widget.h
  widget_updater.h
)

add_library(onyx_feed_reader_lib
  add_feed_dialog.cpp
  article.cpp
  article_list_model.cpp
  article_list_page.cpp
  article_page.cpp
  database.cpp
  feed.cpp
  feed_fetcher.cpp
  feed_list_model.cpp
  feeds_page.cpp
  init.cpp
  main_widget.cpp
  rss_feed_parser.cpp
  widget_updater.cpp
  util.cpp
  ${MOC_SRCS}
)

QT4_ADD_RESOURCES(feedreader_RC ${feedreader_RCS})

target_link_libraries(onyx_feed_reader_lib  ${QT_LIBRARIES} ${ONYX_LIBS} ${feedreader})
strict_warning(onyx_feed_reader_lib)

add_executable(onyx_feed_reader feed_reader.cpp ${feedreader} ${feedreader_RC})
target_link_libraries(onyx_feed_reader  onyx_feed_reader_lib ${QT_LIBRARIES})
strict_warning(onyx_feed_reader)
