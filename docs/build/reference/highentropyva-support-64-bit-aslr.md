---
title: "/HIGHENTROPYVA (Compatibilidad con ASLR de 64 bits) | Microsoft Docs"
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
ms.assetid: fe35f9f7-d28e-4694-9aeb-a79db06168e0
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /HIGHENTROPYVA (Compatibilidad con ASLR de 64 bits)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica que la imagen ejecutable es compatible con la selección aleatoria del diseño del espacio de direcciones \(ASLR\) de 64 bits de alta entropía.  
  
## Sintaxis  
  
```  
/HIGHENTROPYVA[:NO]  
```  
  
## Comentarios  
 De forma predeterminada, \/HIGHENTROPYVA está activado para las imágenes ejecutables de 64 bits.  No es aplicable a imágenes ejecutables de 32 bits.  Para habilitar esta opción, \/DYNAMICBASE también debe estar activado.  
  
 \/HIGHENTROPYVA modifica el encabezado de un archivo .dll o .exe para indicar si se admite ASLR con direcciones de 64 bits.  Cuando esta opción está establecida en un ejecutable y todos los módulos de los que este depende, un sistema operativo compatible con ASLR de 64 bits puede reorganizar los segmentos de la imagen ejecutable en tiempo de carga mediante el uso de direcciones aleatorias en un espacio de direcciones virtuales de 64 bits.  Este gran espacio de direcciones dificulta a un atacante la tarea de adivinar la ubicación de un área de memoria específica.  
  
### Para establecer esta opción del vinculador en Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Expanda el nodo **Propiedades de configuración**.  
  
3.  Expanda el nodo **Vinculador**.  
  
4.  Seleccione la página de propiedades **Línea de comandos**.  
  
5.  En **Opciones adicionales**, escriba `/HIGHENTROPYVA` o `/HIGHENTROPYVA:NO`.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)