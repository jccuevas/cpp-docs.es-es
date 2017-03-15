---
title: "Error del compilador de recursos RC2104 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RC2104"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC2104"
ms.assetid: 792a3bd8-cb4c-4817-b288-4ce37082b582
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador de recursos RC2104
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

palabra clave o nombre de clave sin definir: clave  
  
 La palabra clave o el nombre de clave especificados no se ha definido.  
  
 A menudo, este error se debe a un error de escritura en la definición del recurso o en el archivo de encabezado incluido.  También puede deberse a que falta un archivo de encabezado.  
  
 Para corregir el problema, busque el archivo de encabezado que debe contener la palabra clave o el nombre de clave definidos y compruebe que se han incluido en el archivo de recursos, y que la palabra clave o el nombre de clave están escritos correctamente.  Si el proyecto se creó con un encabezado precompilado y posteriormente lo eliminó, asegúrese de que el archivo de recursos sigue incluyendo los encabezados necesarios.  
  
 Para comprobar las palabras clave y los nombres de clave definidos en el archivo de recursos, en Visual Studio, abra la ventana **Vista de recursos** \(en la barra de menús, seleccione **Vista**, **Vista de recursos**\) y, a continuación, abra el menú contextual del archivo .rc y elija **Símbolos de recursos** para ver la lista de símbolos definidos.  Para modificar los encabezados incluidos, abra el menú contextual del archivo .rc y elija **Archivos de inclusión de recursos**.  
  
 Si aparece este mensaje:  
  
```  
undefined keyword or key name: MFT_STRING   
```  
  
 abra \\MCL\\MFC\\Include\\AfxRes.h y agregue esta directiva Include:  
  
```  
#include <winresrc.h>  
```