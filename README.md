# Assignment-1

library(shiny)
ui <- fluidPage(
  # App title ----
  titlePanel("Shiny App"),
      
      # Input: Slider for the mean ----
      sliderInput(inputId = "mean",
                  label = "Mean",
                  min = 0,
                  max = 100,
                  value = 50),
 
      # Input: Slider for the sd ----
      sliderInput(inputId = "sd",
                  label= "SD",
                  min= 1,
                  max= 10,
                  value= 5),   
      
      
      numericInput(inputId = "Sample",
                   label="Number of Random Samples",
                   min=1,
                   max=100,
                   value= 50),
      plotOutput(outputId = "histogram")
      
    )
    
server <- function(input, output){
  output$histogram <- renderPlot({
    hist(rnorm(input$Sample, input$mean, input$sd), main = "Sample Distribution", xlab = "Sample Value")
  })
}
shinyApp(ui = ui, server = server)
