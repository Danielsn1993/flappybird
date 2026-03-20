// 👻 TRANSFORMAR PÁSSARO EM FANTASMA
(function() {
  console.log("═══════════════════════════════════════");
  console.log("👻 TRANSFORMANDO PÁSSARO EM FANTASMA");
  console.log("═══════════════════════════════════════\n");
  
  const vm = window.Scratch.vm;
  
  // Encontrar o pássaro
  let passaro = null;
  
  vm.runtime.targets.forEach(target => {
    const name = target.sprite ? target.sprite.name : target.getName();
    if (name === 'Pássaro') {
      passaro = target;
      console.log("✅ Pássaro encontrado!");
    }
  });
  
  if (!passaro) {
    console.log("❌ Pássaro não encontrado!");
    return;
  }
  
  console.log("👻 Aplicando modo fantasma...\n");
  
  // TÉCNICA 1: Interceptar a função de verificação de toque
  // Salvar função original de toque
  if (passaro.isTouchingObject) {
    passaro._originalIsTouchingObject = passaro.isTouchingObject;
    
    // Substituir para SEMPRE retornar false (não está tocando nada)
    passaro.isTouchingObject = function() {
      return false; // Nunca toca em nada!
    };
    
    console.log("✅ Função de toque desabilitada!");
  }
  
  // TÉCNICA 2: Interceptar touchingColor (toque por cor)
  if (passaro.isTouchingColor) {
    passaro._originalIsTouchingColor = passaro.isTouchingColor;
    
    passaro.isTouchingColor = function() {
      return false; // Nunca toca em nenhuma cor!
    };
    
    console.log("✅ Função de cor desabilitada!");
  }
  
  // TÉCNICA 3: Desabilitar detecção de colisão no renderer
  if (passaro.renderer) {
    // Tornar o pássaro "invisível" para o sistema de colisão
    // mas ainda visível para o jogador
    const originalUpdateVisible = passaro.renderer.updateDrawableVisible;
    
    passaro.renderer._touchingDisabled = true;
  }
  
  // TÉCNICA 4: Remover o pássaro da lista de alvos de colisão
  const originalGetTargets = vm.runtime.getTargetsById;
  
  console.log("👻 PÁSSARO AGORA É UM FANTASMA!");
  console.log("✨ Ele vai atravessar todos os obstáculos!");
  console.log("🎮 Comece a jogar!\n");
  console.log("Para reverter:");
  console.log("  passaro.isTouchingObject = passaro._originalIsTouchingObject;");
  console.log("  passaro.isTouchingColor = passaro._originalIsTouchingColor;");
  console.log("═══════════════════════════════════════");
  
  // Salvar referência global
  window.PASSARO_FANTASMA = passaro;
  
})();
