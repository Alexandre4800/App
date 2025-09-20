
# GeMap - Como gerar o APK (instruções prontas)

**Resumo:** Eu não consigo compilar o APK diretamente neste ambiente (não há Android SDK / Gradle instalado aqui).  
Porém, seu projeto já contém um workflow do GitHub Actions que **monta o APK de debug** automaticamente. Eu preparei este pacote com instruções para você subir ao GitHub e obter o APK:

## Opção A — Usar GitHub Actions (recomendado)
1. Crie um novo repositório no GitHub (por exemplo `GeMap`).
2. No seu computador, abra um terminal na pasta do projeto e rode:
   ```bash
   git init
   git add .
   git commit -m "Initial commit for GeMap"
   git branch -M main
   git remote add origin https://github.com/<seu-usuario>/<repo>.git
   git push -u origin main
   ```
3. Vá em **Actions** no GitHub e aguarde o workflow `Android CI` rodar.  
   - O workflow existente já faz `./gradlew :app:assembleDebug` e faz upload do `app-debug.apk` como artefato.
4. Quando o job terminar, vá em **Actions → Android CI → (run) → Artifacts** e baixe `GeMap-apk`.
5. Transfira o APK para seu celular e instale (habilite instalação de fontes desconhecidas, se necessário).

> Observação: se o workflow falhar por falta de licença do Android SDK, posso ajustar o workflow. Envie a saída do job (log) aqui que eu corrijo.

## Opção B — Compilar localmente (no seu PC)
Pré-requisitos:
- JDK 11 ou 17
- Android SDK (com plataformas e build-tools compatíveis)
- `ANDROID_HOME` ou `ANDROID_SDK_ROOT` configurado
- `gradle` ou usar o wrapper `./gradlew`

No terminal (na pasta do projeto):
```bash
# Tornar o wrapper executável se necessário
chmod +x gradlew

# Build debug APK
./gradlew :app:assembleDebug
# APK gerado em:
# app/build/outputs/apk/debug/app-debug.apk
```

## Assinatura / Release
- O APK gerado com `assembleDebug` é assinada com a chave de debug (instalável para testes).
- Para publicar na Play Store ou gerar um release assinado, eu preciso do *keystore* (arquivo .jks) e da senha, ou posso gerar instruções para você criar um keystore e configurar assinatura no `build.gradle.kts`.

## Se precisar, eu posso:
- Ajustar o workflow do GitHub Actions para assembleRelease (assinatura) — se você fornecer o keystore (via GitHub Secrets).
- Corrigir erros de configuração no projeto (namespace, package, versão) caso o job falhe. Para isso é só me encaminhar o log do Actions.

---

Se quiser, eu já subi um arquivo ZIP preparado com este README (pronto para enviar ao GitHub). Use-o se preferir — link abaixo.
