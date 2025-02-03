Template React Native para Taro
====

## Requisitos

1. Taro: `@tarojs/cli@^3.5.0`
2. Framework: 'react'

## Início Rápido

### Instalação das Bibliotecas React Native
> Instale as dependências peer de `@tarojs/taro-rn`, `@tarojs/components-rn` e `@tarojs/router-rn`. Esse comando também executa o `post-install`. Lembre-se de modificar e executar o script `upgradePeerdeps` sempre que alterar a versão do Taro.
> 
> **Execute este script logo após a criação do projeto.**

`yarn upgradePeerdeps`

### Instalação de Pods
> Execute este script ao adicionar ou atualizar uma biblioteca React Native.
> 
> Consulte [pod-install](https://www.npmjs.com/package/pod-install) para mais informações.

`yarn podInstall`

### Iniciar Aplicativo iOS

`yarn ios`

### Iniciar Aplicativo Android

`yarn android`

### Iniciar o Bundler

`yarn start`

### Mais Informações

1. [Processo de Desenvolvimento do Taro React Native](https://taro-docs.jd.com/taro/docs/react-native)
2. [GitHub](https://github.com/NervJS/taro)

## Release

### Gerar Pacote para iOS

`yarn build:rn --platform ios`

### Gerar Pacote para Android

`yarn build:rn --platform android`

### Publicar Aplicativo iOS

Consulte [publishing-to-app-store](https://reactnative.cn/docs/publishing-to-app-store) para mais detalhes.

### Publicar APK Android

Consulte [signed-apk-android](https://reactnative.cn/docs/signed-apk-android) para mais detalhes.

## GitHub Workflows
> Utilize o GitHub Actions para construir seus aplicativos. Este template já inclui uma configuração básica para GitHub Actions.

Consulte a pasta [.github/workflows](.github/workflows) para mais detalhes.

### Eventos

Por padrão, são geradas builds de debug e release para Android e iOS quando você realiza push ou pull request na branch master. Customize seus fluxos de trabalho modificando os arquivos dentro de [.github/workflows](.github/workflows).

Consulte [events-that-trigger-workflows](https://docs.github.com/en/actions/reference/events-that-trigger-workflows)

### iOS

#### Configuração

Altere os itens de configuração abaixo para empacotar e publicar seu aplicativo.

> [.github/workflows/assemble_ios_debug.yml](.github/workflows/assemble_ios_debug.yml)
> [.github/workflows/assemble_ios_release.yml](.github/workflows/assemble_ios_release.yml)

```yml
env:
  APP_ID: com.taro.demo           # Identificador do Bundle do aplicativo
  APP_NAME: Taro Demo             # Nome de exibição do seu aplicativo
  VERSION_NUMBER: 1.0.0           # Número da versão do aplicativo
  BUILD_NUMBER: 1.0.0.0           # Número da build (utilizado apenas para release)
  TEAM_ID: XXXXXXXXXX             # ID da equipe (necessário para atualizações)
  PROVISIONING_PROFILE_SPECIFIER: Product_profile  # Nome do provisioning profile para assinatura do código
  CODE_SIGN_IDENTITY: iPhone Distribution         # Tipo de identidade para assinatura (iPhone Developer ou iPhone Distribution)
  SIGNING_CERTIFICATE_P12_DATA: ${{secrets.RELEASE_SIGNING_CERTIFICATE_P12_DATA}}
  SIGNING_CERTIFICATE_PASSWORD: ${{secrets.RELEASE_SIGNING_CERTIFICATE_PASSWORD}}
  PROVISIONING_PROFILE_DATA: ${{secrets.RELEASE_PROVISIONING_PROFILE_DATA}}
  APP_STORE_CONNECT_USERNAME: ${{secrets.APP_STORE_CONNECT_USERNAME}}  # Apple ID da conta de desenvolvedor (apenas para release)
  APP_STORE_CONNECT_PASSWORD: ${{secrets.APP_STORE_CONNECT_PASSWORD}}  # (apenas para release)
```

Valores como ${{secrets.xxxxx}} devem ser gerados manualmente e armazenados nos segredos criptografados do GitHub.

##### SIGNING_CERTIFICATE_P12_DATA

`cat Certificates.p12 | base64 | pbcopy`

##### SIGNING_CERTIFICATE_PASSWORD

Senha utilizada para criptografar o arquivo de certificado (.p12).

##### PROVISIONING_PROFILE_DATA

`cat profile.mobileprovision | base64 | pbcopy`

##### APP_STORE_CONNECT_PASSWORD

Este segredo deve conter uma senha específica para sua conta Apple ID. Siga [estas instruções](https://support.apple.com/en-us/HT204397) para criá-la.

#### Leia Mais

1. [Como publicar um aplicativo iOS na TestFlight ou na App Store utilizando GitHub Actions](https://betterprogramming.pub/deploy-an-ios-app-to-testflight-or-the-app-store-using-github-actions-c4d7082b1430)
2. [Secrets Criptografados](https://docs.github.com/en/actions/reference/encrypted-secrets)
3. [Fastlane](https://docs.fastlane.tools/)

### Android

#### Configuração

Altere os itens de configuração abaixo para empacotar e publicar seu aplicativo.

> [.github/workflows/assemble_android_debug.yml](.github/workflows/assemble_android_debug.yml)
> [.github/workflows/assemble_android_release.yml](.github/workflows/assemble_android_release.yml)

```yml
env:
  APP_ID: com.taro.demo            # Identificador do Bundle do aplicativo
  APP_NAME: Taro Demo              # Nome de exibição do seu aplicativo
  APP_ICON: ic_launcher            # Ícone do aplicativo
  APP_ROUND_ICON: ic_launcher_round  # Ícone arredondado do aplicativo
  APP_ABI_FILTERS: armeabi-v7a, arm64-v8a  # Filtros de ABI do aplicativo
  VERSION_NAME: 1.0.0              # Nome da versão
  VERSION_CODE: 10               # Código da versão
  KEYSTORE_FILE: debug.keystore    # Arquivo keystore
  KEYSTORE_PASSWORD: android       # Senha da keystore
  KEYSTORE_KEY_ALIAS: androiddebugkey  # Alias da chave na keystore
  KEYSTORE_KEY_PASSWORD: android   # Senha da chave na keystore
```

Para garantir a segurança do seu aplicativo, gere um novo arquivo .keystore e armazene a senha nos segredos criptografados do GitHub.

#### Leia Mais

1. [Assinatura de Aplicativos](https://developer.android.com/studio/publish/app-signing)
2. [Secrets Criptografados](https://docs.github.com/en/actions/reference/encrypted-secrets)

## Links

1. [Código-fonte do template](https://github.com/NervJS/taro-project-templates/tree/v3.1/react-native)
2. [Projeto Exemplo](https://github.com/wuba/taro-react-native/tree/playground)

# Taro

O Taro é uma ferramenta de código aberto que permite criar aplicações que funcionam em diversos dispositivos e plataformas, como Mini Programas, sites e aplicativos móveis.

## Sumário

1. [O que é o Taro?](https://www.notion.so/165ffac4b8f2807f9a3fe29769c4e765?pvs=21)
2. [Como Começar](https://www.notion.so/165ffac4b8f2807f9a3fe29769c4e765?pvs=21)
3. [Exemplos e Comunidade](https://www.notion.so/165ffac4b8f2807f9a3fe29769c4e765?pvs=21)
4. [Status do Projeto](https://www.notion.so/165ffac4b8f2807f9a3fe29769c4e765?pvs=21)
5. [Casos de Uso](https://www.notion.so/165ffac4b8f2807f9a3fe29769c4e765?pvs=21)
6. [Como Contribuir](https://www.notion.so/165ffac4b8f2807f9a3fe29769c4e765?pvs=21)
7. [Relatar Problemas e Dar Sugestões](https://www.notion.so/165ffac4b8f2807f9a3fe29769c4e765?pvs=21)
8. [Agradecimentos Especiais](https://www.notion.so/165ffac4b8f2807f9a3fe29769c4e765?pvs=21)
9. [Quem Contribuiu](https://www.notion.so/165ffac4b8f2807f9a3fe29769c4e765?pvs=21)
10. [Planejamento do Projeto](https://www.notion.so/165ffac4b8f2807f9a3fe29769c4e765?pvs=21)
11. [Histórico de Mudanças](https://www.notion.so/165ffac4b8f2807f9a3fe29769c4e765?pvs=21)
12. [Comunidade de Desenvolvimento](https://www.notion.so/165ffac4b8f2807f9a3fe29769c4e765?pvs=21)
13. [Licença](https://www.notion.so/165ffac4b8f2807f9a3fe29769c4e765?pvs=21)

---

## O que é o Taro?

O Taro permite que você escreva um único conjunto de código para criar aplicações que rodem em diversos ambientes, tais como:

- **Mini Programas:** Aplicativos leves que funcionam em plataformas como WeChat, JD, Baidu, Alipay, ByteDance e QQ.
- **H5:** Sites acessíveis de qualquer navegador.
- **Aplicativos Móveis:** Apps nativos, como os desenvolvidos com React Native.

Ao escrever o código apenas uma vez, o Taro adapta sua aplicação para funcionar em todas essas plataformas, facilitando e agilizando o desenvolvimento.

### Atualização do Taro

Se você já utiliza uma versão anterior do Taro (1 ou 2) e deseja migrar para a versão 3, consulte o [Guia de Atualização do Taro](https://docs.taro.zone/blog/2020-09-01-taro-versions) para obter mais detalhes.

---

## Como Começar

- [**Comece em 5 minutos**](https://docs.taro.zone/docs/guide): Um guia rápido para iniciar com o Taro.
- [**awesome-taro**](https://github.com/NervJS/awesome-taro): Uma lista com diversos recursos e exemplos sobre o Taro.

---

## Exemplos e Comunidade

### Mercado de Componentes do Taro

Explore o [Mercado de Componentes Taro](http://taro-ext.jd.com/), onde você pode encontrar e compartilhar componentes prontos para uso em suas aplicações.

### Bibliotecas UI

As bibliotecas UI reúnem coleções de componentes que facilitam a criação das interfaces dos aplicativos. Confira alguns exemplos:

| **Nome** | **Link** | **Descrição** | **Framework Suportado** | **Versões do Taro Suportadas** |
| --- | --- | --- | --- | --- |
| [taro-ui](https://github.com/NervJS/taro-ui) | [taro-ui.jd.com](https://taro-ui.jd.com/#/) | Biblioteca de componentes compatível com diversas plataformas | React | Taro 1, 2 e 3 |
| [NutUI](https://github.com/jdf2e/nutui) | [nutui.jd.com](https://nutui.jd.com/#/) | Biblioteca de componentes para dispositivos móveis com Vue, ao estilo JD.com | Vue3 | Taro 3 |
| [taroify](https://github.com/mallfoundry/taroify) | [taroify.github.io](https://taroify.github.io/taroify.com/introduce/) | Conjunto de componentes para Mini Programas, inspirado no Vant | React | Taro 3 |
| [@antmjs/vantui](https://github.com/AntmJS/vantui) | [antmjs.github.io](https://antmjs.github.io/vantui/#/home) | Biblioteca de componentes baseada no VantWeapp, compatível com Taro e React | React | Taro 3 |
| [Tard](https://github.com/jd-antelope/tard) | [tard-ui.selling.cn](https://tard-ui.selling.cn/) | Conjunto de componentes React para diversas plataformas | React | Taro 3 |
| [duxui](https://github.com/duxapp/duxui) | [duxapp.cn](https://duxapp.cn/docs/duxui/start/) | Biblioteca de componentes para Mini Programas, React Native, HarmonyOS e H5 | React | Taro 4 |

---

---

## Como Contribuir

### Junte-se à Comunidade

Ajude a aprimorar o Taro participando do desenvolvimento colaborativo.

Acesse [este link](https://github.com/NervJS/taro/issues/4714) para mais informações.

### Contribua com Código

Se deseja colaborar escrevendo código, siga estes passos:

1. Leia o [Guia de Contribuição](https://nervjs.github.io/taro/docs/CONTRIBUTING.html) para conhecer as regras.
2. Planeje a implementação de novas funcionalidades conforme o [Processo RFC](https://github.com/NervJS/taro-rfcs), onde suas ideias são discutidas com a comunidade antes da implementação.

---

## Relatar Problemas e Dar Sugestões

Caso encontre algum problema ou tenha sugestões para melhorar o Taro:

- [Reporte um problema](https://nervjs.github.io/taro-issue-helper/)
- Confira dicas em:
    - [A Arte de Fazer Perguntas](https://github.com/ryanhanwu/How-To-Ask-Questions-The-Smart-Way)
    - [Como Reportar Bugs Eficientemente](http://www.chiark.greenend.org.uk/%7Esgtatham/bugs-cn.html)

Você também pode ajudar financiando a resolução de issues:

<div style="text-align:center">
  <a href="https://issuehunt.io/repos/128624453">
    <img src="https://issuehunt.io/static/embed/issuehunt-button-v1.svg" alt="Financie issues neste repositório" />
  </a>
</div>

---

## Planejamento do Projeto

Confira os [Marcos Importantes](https://github.com/NervJS/taro/milestones) para ficar por dentro das próximas atualizações.

---

## Histórico de Mudanças

As alterações no projeto seguem as [Convenções de Mensagens de Commit do Angular](https://gist.github.com/stephenparish/9941e89d80e2bc58a153).

Para mais detalhes, veja a seção [Releases](https://github.com/NervJS/taro/releases).

---

## Comunidade de Desenvolvimento

Quer conversar com outros desenvolvedores e tirar dúvidas?

Entre no [Grupo Oficial no WeChat](https://github.com/NervJS/taro/issues/198).

---

### Dicas e Conceitos

- **Código Aberto (Open-source):** Qualquer pessoa pode visualizar, utilizar e modificar o código do Taro.
- **Multiplataforma:** Escreva o código apenas uma vez e a aplicação funcionará em diversos sistemas, como sites e aplicativos móveis.
- **Framework:** Uma estrutura que organiza e agiliza o desenvolvimento de software.
