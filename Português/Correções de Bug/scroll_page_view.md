# Adicionando ScrollConfiguration para Usar PageView no Flutter Desktop


* No Flutter, o PageView é uma widget bastante utilizada para criar interfaces de navegação paginada. No entanto, há uma diferença importante entre as versões móveis e desktop do Flutter no que diz respeito ao comportamento de rolagem.

* Para Aplicações Móveis
Em dispositivos móveis, o PageView funciona perfeitamente sem configurações adicionais para rolagem, pois o comportamento de rolagem padrão já está otimizado para toque e arrasto.

* Para Aplicações Desktop
Em ambientes de desktop, é necessário adicionar uma configuração extra para garantir que o PageView funcione corretamente com diferentes dispositivos de entrada, como o mouse e o touchpad. Isso é feito usando o widget ScrollConfiguration.

* Passo a Passo para Configurar o PageView no Flutter Desktop
  Aqui está um tutorial sobre como adicionar o ScrollConfiguration para que o PageView funcione corretamente em aplicações desktop:
  
  - Abra seu projeto Flutter e localize o arquivo onde deseja adicionar o PageView.
  
  - Adicione o widget ScrollConfiguration ao redor do seu PageView para definir o comportamento de rolagem.
  
  - Configure o comportamento de rolagem para aceitar entradas de dispositivos como toque e mouse.
  
  - Aqui está um exemplo completo de como fazer isso:


```
class PageViewExample extends StatelessWidget {
  final PageController pageController = PageController();

  @override
  Widget build(BuildContext context) {
    return ScrollConfiguration(
      behavior: ScrollConfiguration.of(context).copyWith(
        dragDevices: {
          PointerDeviceKind.touch,
          PointerDeviceKind.mouse,
        },
      ),
      child: PageView(
        controller: pageController,
        scrollDirection: Axis.horizontal,
        children: [
          Container(
            height: 200,
            width: 200,
            color: Colors.blue,
            child: Center(
              child: Text('1', style: TextStyle(color: Colors.white, fontSize: 24)),
            ),
          ),
          Container(
            height: 200,
            width: 200,
            color: Colors.red,
            child: Center(
              child: Text('2', style: TextStyle(color: Colors.white, fontSize: 24)),
            ),
          ),
          Container(
            height: 200,
            width: 200,
            color: Colors.grey,
            child: Center(
              child: Text('3', style: TextStyle(color: Colors.white, fontSize: 24)),
            ),
          ),
        ],
      ),
    );
  }
}
```

* Explicação:
  - ScrollConfiguration: Envolve o PageView para personalizar o comportamento de rolagem.
  - behavior: Utiliza a configuração de rolagem padrão do contexto (ScrollConfiguration.of(context)) e modifica a lista de dispositivos de entrada (dragDevices), permitindo o toque e o mouse.
  - PageView: Define o controle de páginas e as páginas exibidas.
  - Com essa configuração, seu PageView deve funcionar de forma suave e responsiva tanto em dispositivos de toque quanto em dispositivos de entrada de desktop, como o mouse.