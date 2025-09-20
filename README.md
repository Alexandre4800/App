# GeMap (skeleton project)

Este repositório contém um esqueleto de projeto Android para o app **GeMap**.
Ele inclui:
- Menu lateral/opções com botão de emergência (Polícia 190, SAMU 192, Bombeiros 193)
- Permissões básicas (localização, chamadas)
- Estrutura pronta para adicionar Google Maps, histórico, favoritos e integração com assistente de voz
- GitHub Actions workflow para compilar APK automaticamente

**Importante:** Este é um projeto *skeleton*. Para gerar o APK é necessário:
1. Abrir o projeto no Android Studio (recomendo Android Studio Flamingo ou mais recente).
2. Configurar `google-services` / API keys para Google Maps (se for usar Map SDK).
3. Ajustar integração com assistente de voz (Gemini/ChatGPT) e prover chaves/endpoint seguro.
4. Conceder permissões de CALL_PHONE e ACCESS_FINE_LOCATION no dispositivo ao instalar.
