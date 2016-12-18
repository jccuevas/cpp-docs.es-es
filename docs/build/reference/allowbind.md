---
title: "/ALLOWBIND | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/allowbind"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ALLOWBIND (opción de editbin)"
  - "/ALLOWBIND (opción de editbin)"
  - "-ALLOWBIND (opción de editbin)"
ms.assetid: eaadbb8c-4339-4281-9a75-3a1ce2352ff8
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /ALLOWBIND
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica si el archivo DLL puede enlazarse.  
  
```  
  
/ALLOWBIND[:NO]  
  
```  
  
## Comentarios  
 Las opciones establecidas de **\/ALLOWBIND** un bit en un encabezado de DLL que indica a Bind.exe que la imagen se permite ser enlazada.  El enlace puede permitir que una imagen cargue más rápidamente cuando el cargador no tiene que rebase y realizar la corrección de la dirección para cada archivo DLL hace referencia.  Puede que no desee DLL que se enlazará si ha sido digitalmente firmar\- enlace reemplaza la firma.  El enlace no tiene ningún efecto si la distribución aleatoria \(ASLR\) de diseño del espacio de direcciones está habilitado para la imagen utilizando **\/DYNAMICBASE** en las versiones de Windows que ASLR admiten.  
  
 Utilice **\/ALLOWBIND:NO** para evitar que Bind.exe enlace DLL.  
  
 Para obtener más información, vea la opción del vinculador [\/ALLOWBIND](../../build/reference/allowbind-prevent-dll-binding.md) .  
  
## Vea también  
 [Opciones de EDITBIN](../../build/reference/editbin-options.md)