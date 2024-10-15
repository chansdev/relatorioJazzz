# RELATÓRIO DA SEMANA

## COISAS QUE APRENDI:
*Dia 14/10 até 18/10*

### MODAL
Menu que aparece quando você clica no botão de login.  
   
<img src="https://github.com/user-attachments/assets/3791cf3c-46e5-4eef-ae22-882b88cfc63e" width=430px height=350px>

#### Como eu fiz:
Criei um elemento no HTML, estilizei ele e o deixei oculto. Aí, no JavaScript, criei uma função que adiciona a classe "ativo" ao elemento, e essa classe faz com que essa tela apareça.  
*Além disso o botão leva para uma página de login caso o JavaScript não tenha carregado para o usuário*

  ```js
    const botaoAbrir = document.querySelector('[data-modal="abrir"]');
    const botaoFechar = document.querySelector('[data-modal="fechar"]');
    const containerModal = document.querySelector('[data-modal="container"]');
    
    if (botaoAbrir && botaoFechar && containerModal) {
      function toggleModal(event) {
        event.preventDefault();
        containerModal.classList.toggle("ativo");
      }
    
      function cliqueFora(event) {
        if (event.target == this) {
          toggleModal(event);
        }
      }
    
      botaoAbrir.addEventListener("click", toggleModal);
      botaoFechar.addEventListener("click", toggleModal);
      containerModal.addEventListener("click", cliqueFora);
    }
  ```

### TOOLTIP
Descrição que aparece de forma personalizada ao colocar o mouse em cima de uma imagem.  
   
<img src="https://github.com/user-attachments/assets/d77d39ab-bc00-40f0-b0c4-3c71b98a7418" width=430px height=350px>

### Como eu fiz:
Criei uma função que faz com que um elemento com a classe "tooltip" seja criado ao passar o mouse na imagem e estilizei a classe para que ficasse do jeito desejado. Depois criei um objeto com uma função "handleEvent" que faça com que o elemento seja deletado após tirar o mouse de cima da imagem. E depois disso criei outro objeto que faça com que o elemento siga a posição do mouse.

  ```js
    const tooltips = document.querySelectorAll("[data-tooltip]");

    tooltips.forEach((item) => {
      item.addEventListener("mouseover", onMouseOver);
    });
  
    function onMouseOver(event) {
      const tooltipBox = criarTooltip(this);
  
      onMouseMove.tooltipBox = tooltipBox;
      this.addEventListener("mousemove", onMouseMove);
  
      onMouseLeave.tooltipBox = tooltipBox;
      onMouseLeave.element = this;
      this.addEventListener("mouseleave", onMouseLeave);
    }
  
    const onMouseLeave = {
      handleEvent() {
        this.tooltipBox.remove();
        this.element.removeEventListener("mouseleave", onMouseLeave);
        this.element.removeEventListener("mousemove", onMouseMove);
      },
    };
  
    const onMouseMove = {
      handleEvent(event) {
        this.tooltipBox.style.top = event.pageY + 20 + "px";
        this.tooltipBox.style.left = event.pageX + 20 + "px";
      },
    };
  
    function criarTooltip(element) {
      const tooltipBox = document.createElement("div");
      const text = element.getAttribute("aria-label");
      tooltipBox.classList.add("tooltip");
      tooltipBox.innerText = text;
      document.body.appendChild(tooltipBox);
      return tooltipBox;
    }
  ```

### DROPDOWN MENU
Menu de navegação que aparece ao clicar ou passar o mouse em cima de um botão.  
   
<img src="https://github.com/user-attachments/assets/6e66445d-2e73-429b-a48a-ae7509f6eb6f" width=430px height=350px>

### CRONOMETRO
Cronometro funcional.  

<img src="https://github.com/user-attachments/assets/6ced5b46-c28e-4ace-8bda-23f289468179" width=430px height=350px>  

### Como eu fiz:
Fiz os elementos no HTML (botões e texto) e os selecionei no algorítimo.
Assim adicionei um indentificador de evento que verifica quando o botão foi clicado. Se o botão for precionado ele ativa uma função que muda o conteúdo do texto de acordo com o tempo pressuposto na função setInterval. No outro botão tambem tem indentificador de evento. O primeiro pausa o setInterval e o outro, ao invés de intentificar se ele foi clicado, indentifica se ele foi clicado duas vezes e assim reinicia a contagem de tempo.
