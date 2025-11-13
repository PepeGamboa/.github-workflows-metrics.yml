name: Metrics

on:
  schedule:
    - cron: "0 0 * * *"  # Ejecuta diariamente a medianoche
  workflow_dispatch:

permissions:
  contents: write

jobs:
  github-metrics:
    runs-on: ubuntu-latest
    
    steps:
      - uses: lowlighter/metrics@latest
        with:
          token: ${{ secrets.METRICS_TOKEN }}
          user: PepeGamboa
          template: classic
          base: header, activity, community, repositories, metadata
          
          # Habilita el plugin de hábitos con gráficos
          plugin_habits: yes
          plugin_habits_charts: yes
          plugin_habits_days: 14
          plugin_habits_facts: yes
