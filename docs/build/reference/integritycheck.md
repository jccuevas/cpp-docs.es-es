---
title: "/INTEGRITYCHECK | Microsoft Docs"
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
  - "/INTEGRITYCHECK"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/INTEGRITYCHECK editbin (opciones)"
  - "INTEGRITYCHECK editbin (opciones)"
  - "-INTEGRITYCHECK editbin (opciones)"
ms.assetid: 2a293705-4396-421b-a5a5-693b4b867a85
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /INTEGRITYCHECK
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica que la firma digital de la imagen binaria debe estar activada en tiempo de carga.  
  
```  
  
/INTEGRITYCHECK[:NO]  
  
```  
  
## Comentarios  
 En el encabezado de archivo o de archivo DLL ejecutable, esta opción establece un marcador que requiere una comprobación de firma digital realizada por el administrador de memoria para cargar la imagen en Windows.  Las versiones de Windows anteriores a Windows Vista omiten esta marca.  Esta opción se debe establecer para archivos DLL de 64 bits que implementan código en modo kernel y se recomienda para todos los controladores de dispositivo.  Para obtener más información, vea el [tutorial de firma de código en modo kernel](http://go.microsoft.com/fwlink/?linkid=237093) en el sitio web de MSDN.  
  
## Vea también  
 [Opciones de EDITBIN](../../build/reference/editbin-options.md)