---
title: "/GUARD (habilitar comprobaciones de restricci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 72758e23-70ac-4616-94d7-d767477406d1
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /GUARD (habilitar comprobaciones de restricci&#243;n)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica la compatibilidad con las comprobaciones de Protección de flujo de control en la imagen ejecutable.  
  
## Sintaxis  
  
```  
/GUARD:{CF|NO}  
```  
  
## Comentarios  
 Cuando se especifica \/GUARD:CF, el vinculador modifica el encabezado de un archivo .dll o .exe para indicar la compatibilidad con las comprobaciones en tiempo de ejecución de Protección de flujo de Control \(CFG\).  El vinculador también agrega los datos requeridos de dirección de destino del flujo de control al encabezado.  De forma predeterminada, \/GUARD:CF está deshabilitada.  Se puede deshabilitar explícitamente mediante el uso de \/GUARD:NO.  Para que sea eficaz, \/GUARD:CF también requiere la opción del vinculador [\/DYNAMICBASE \(Usar selección aleatoria del diseño del espacio de direcciones\)](../../build/reference/dynamicbase-use-address-space-layout-randomization.md), que está habilitada de forma predeterminada.  
  
 Cuando se compila código fuente mediante el uso de la opción [\/guard:cf](../../build/reference/guard-enable-control-flow-guard.md), el compilador analiza el flujo de control examinando todas las llamadas indirectas en busca de posibles direcciones de destino.  El compilador inserta código para comprobar que la dirección de destino de una instrucción de llamada indirecta está en la lista de direcciones de destino conocidas en tiempo de ejecución.  Si un programa no supera una comprobación de CFG en tiempo de ejecución, los sistemas operativos compatibles con CFG lo detienen.  Esto hace más difícil que un atacante pueda ejecutar código malintencionado mediante el uso de datos dañados para cambiar un destino de llamada.  
  
 La opción \/GUARD:CF debe especificarse tanto en el compilador como en el vinculador para crear imágenes ejecutables con protección de flujo de control \(CFG\).  El código compilado pero no vinculado mediante \/GUARD:CF aumenta el costo de comprobaciones en tiempo de ejecución, pero no habilita la protección CFG.  Cuando se especifica la opción de \/GUARD:CF para el comando `cl` para compilar y vincular en un solo paso, el compilador pasa la marca al vinculador.  Si se establece la propiedad **Protección de flujo de control** en Visual Studio, se pasa la opción \/GUARD:CF al compilador y al vinculador.  Si se han compilado por separado las bibliotecas o archivos de objetos, la opción debe especificarse explícitamente en el comando `link`.  
  
### Para establecer esta opción del vinculador en Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, consulte [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Expanda **Propiedades de configuración**, **Vinculador** y seleccione **Línea de comandos**.  
  
3.  En **Opciones adicionales**, escriba `/GUARD:CF`.  
  
## Vea también  
 [\/guard \(habilitar Protección de flujo de control\)](../../build/reference/guard-enable-control-flow-guard.md)   
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)