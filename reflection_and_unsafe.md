return {
  "stevearc/conform.nvim",
  opts = {
    formatters_by_ft = {
      lua = { "stylua" },
      -- Conform will run multiple formatters sequentially
      python = { "isort", "black" },
      -- You can customize some of the format options for the filetype (:help conform.format)
      rust = { { "rustfmt" }, lsp_fallback = true },
      -- Conform will run the first available formatter
      javascript = { { "prettierd", "prettier" }, stop_after_first = true },
      -- Go
      go = { { "gofumpt", "goimports" }, stop_after_first = true },
    },
    format_on_save = {
      lsp_fallback = true, -- Use LSP formatting if no conform formatter is available
      timeout_ms = 1000,   -- Timeout for formatting in milliseconds
    },
  },
  config = function(_, opts)
    require("conform").setup(opts)
    -- Keymap for conform.format()
    vim.keymap.set("n", "<leader>fm", function()
      require("conform").format({ async = true })
    end, { desc = "Format with Conform" })

    -- Remove format on save autocommand; formatting only runs on keybind
  end,
}
