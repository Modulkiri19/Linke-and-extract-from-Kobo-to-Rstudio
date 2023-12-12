# Linke-and-extract-from-Kobo-to-Rstudio


devtools::install_github("asitav-sen/KoboconnectR")

library(KoboconnectR)

kobotools_kpi_data(assetid= "a3cG88pSEwA23UbXXsmkTB", url="kobo.humanitarianresponse.info", uname="makara5", pwd="tuat2022")
get_kobo_token(
  url = "kobo.humanitarianresponse.info",
  uname = "makara5",
  pwd = "tuat2022",
  encoding = "UTF-8"
)

kobotools_api(
  url = "kobo.humanitarianresponse.info",
  simplified = TRUE,
  uname = "makara5",
  pwd = "tuat2022",
  encoding = "UTF-8"
)

kobotools_kpi_data(
  "a3cG88pSEwA23UbXXsmkTB",
  url = "kobo.humanitarianresponse.info",
  uname = "makara5",
  pwd = "tuat2022",
  encoding = "UTF-8"
)

kobo_df_download(
  url = "kobo.humanitarianresponse.info",
  uname = "makara5",
  pwd = "tuat2022",
  assetid = "a3cG88pSEwA23UbXXsmkTB",
  all = "false",
  lang = "_default",
  hierarchy = "false",
  include_grp = "true",
  grp_sep = "/",
  fsep = ";",
  multi_sel = "both",
  media_url = "true",
  fields = NULL,
  sub_ids = NULL,
  sleep = 2
)

T1<- kobo_df_download(
  url = "kobo.humanitarianresponse.info",
  uname = "makara5",
  pwd = "tuat2022",
  assetid = "a3cG88pSEwA23UbXXsmkTB",
  all = "false",
  lang = "_default",
  hierarchy = "false",
  include_grp = "true",
  grp_sep = "/",
  fsep = ";",
  multi_sel = "both",
  media_url = "true",
  fields = NULL,
  sub_ids = NULL,
  sleep = 2
)

table(T1)

kobo_exports(
  url = "kobo.humanitarianresponse.info",
  uname = "makara5",
  pwd = "tuat2022",
  encoding = "UTF-8"
)

data.frame(T1)
View(T1)

kobo_export_create(
  url = "kobo.humanitarianresponse.info",
  uname = "makara5",
  pwd = "tuat2022",
  assetid = "a3cG88pSEwA23UbXXsmkTB",
  type = "csv",
  all = "false",
  lang = "_default",
  hierarchy = "false",
  include_grp = "true",
  grp_sep = "/",
  multi_sel = "both",
  fields = NULL,
  media_url = "true",
  sub_ids = NULL,
  qry = NULL,
  flatten = "true",
  sleep = 2
)

View(T1)
mean(T1$Age)

library(shiny)
library(ggplot2)

fetchAndUpdateData <- function() {
  # Authenticate and fetch data from KoBoToolbox
  data <- T1
  
  # Perform data processing (if required)
  # Example: Convert date strings to proper date format
  data$Date <- as.Date(data$Date, format = "%Y-%m-%d")
  
  # Return processed data
  return(data)
}

ui <- fluidPage(
  plotOutput("myPlot")
)

server <- function(input, output) {
  # Function to render plot based on updated data
  output$myPlot <- renderPlot({
    # Fetch the updated data
    updatedData <- fetchAndUpdateData()
    
    # Create a plot using ggplot or any other library
    # Example: Plotting counts per date
    ggplot(data = updatedData, aes(x = Date)) +
      geom_bar(stat = "count") +
      labs(title = "Data Update Example")
  })
}

shinyApp(ui = ui, server = server)



install.packages("httr")
install.packages("jsonlite")
install.packages("curl")
install.packages("mime")

install.packages("openssl")
install.packages("R6")
install.packages("methods")
install.packages("rlang")
install.packages("purrr")


















