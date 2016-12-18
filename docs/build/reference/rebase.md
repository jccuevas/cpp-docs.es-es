---
title: "/REBASE | Microsoft Docs"
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
  - "/rebase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/REBASE (opción de editbin) [C++]"
  - "direcciones base [C++]"
  - "DLL [C++], vincular"
  - "archivos ejecutables [C++], dirección base"
  - "REBASE (opción de editbin)"
  - "-REBASE (opción de editbin)"
ms.assetid: 3f89d874-af5c-485b-974b-fd205f6e1a4b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /REBASE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/REBASE[:modifiers]  
```  
  
## Comentarios  
 Esta opción establece las direcciones base para los archivos especificados.  EDITBIN asigna nuevas direcciones base en un espacio de direcciones contiguo al tamaño de cada archivo redondeado a los 64 KB más próximos.  Para obtener información detallada acerca de las direcciones base, vea la opción [dirección base](../../build/reference/base-base-address.md) \(\/BASE\) del vinculador.  
  
 Especifique los archivos ejecutables y los archivos DLL del programa en el argumento *files* de la línea de comandos de EDITBIN en el orden en que se van a basar.  Opcionalmente, puede especificar uno o más valores de *modifiers* separados por comas \(**,**\):  
  
|Modificador|Acción|  
|-----------------|------------|  
|BASE**\=***address*|Proporciona una dirección inicial para reasignar direcciones base a los archivos.  Especifique *address* en notación decimal o en la notación del lenguaje C.  Si no se especifica BASE, la dirección base inicial predeterminada será 0x400000.  Si se utiliza DOWN, es necesario especificar BASE; *address* establecerá el final del intervalo de direcciones base.|  
|BASEFILE|Crea un archivo denominado COFFBASE.TXT, que es un archivo de texto con el formato esperado por la opción \/BASE de LINK.|  
|ABAJO|Hace que EDITBIN reasigne las direcciones base hacia abajo a partir de una dirección final.  Los archivos se reasignarán en el orden especificado, con el primer archivo en la dirección más alta posible bajo el final del intervalo de direcciones.  Se debe utilizar con DOWN para garantizar que el espacio de direcciones sea suficiente para establecer la base de los archivos.  Para determinar el espacio de direcciones necesario para los archivos especificados, ejecute EDITBIN con la opción \/REBASE en los archivos y agregue 64 KB al tamaño total mostrado.|  
  
## Vea también  
 [Opciones de EDITBIN](../../build/reference/editbin-options.md)