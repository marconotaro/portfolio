# .Rprofile at root project folder

local({
  sub_dir <- "cancer_subtypes"
  activate_script <- file.path(sub_dir, "renv", "activate.R")

  if (file.exists(activate_script)) {
    # temporarily deactivate pak to avoid subprocess crashing
    # Sys.getenv("RENV_CONFIG_PAK_ENABLED")
    Sys.setenv(RENV_CONFIG_PAK_ENABLED = "FALSE")

    if (requireNamespace("renv", quietly = TRUE)) {
      tryCatch({
        renv::load(sub_dir)
      }, error = function(e) {
        warning("Subdirectory renv failed to load.")
      })
    } else {
      source(activate_script)
    }

    # restore pak
    Sys.setenv(RENV_CONFIG_PAK_ENABLED = 'TRUE')
  }
})
