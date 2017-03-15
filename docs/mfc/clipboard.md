---
title: "Portapapeles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Portapapeles"
  - "Portapapeles, programar"
  - "copiar datos"
  - "cortar y copiar datos"
  - "transferir datos"
ms.assetid: a71b2824-1f14-4914-8816-54578d73ad4e
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Portapapeles
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Esta familia de casos se explica cómo implementar la compatibilidad para el Portapapeles de Windows en aplicaciones MFC.  El Portapapeles de Windows se utiliza de dos maneras:  
  
-   Implementar comandos de menú Edición estándar, como cortar, copiar, pegar y.  
  
-   Implementar la transferencia de datos uniforme con el método de arrastrar y colocar \(OLE\).  
  
 El portapapeles es el método estándar de Windows para transferir datos entre un origen y un destino.  También puede ser útil en operaciones VIEJAS.  Con la llegada de OLE, hay dos mecanismos del portapapeles de Windows.  El Portapapeles de Windows estándar API sigue estando disponible, pero se ha complementado con el mecanismo OLE de transferencia de datos.  La transferencia de datos uniforme\) \(UDT\) admite cortar, copiar, y pegar con el portapapeles y el arrastrar y colocar.  
  
 El portapapeles es un servicio de sistema compartido por la sesión completa de Windows, de modo que no tiene un identificador o una clase de su propio.  Administra el portapapeles con funciones miembro de clases [CWnd](../mfc/reference/cwnd-class.md).  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Cuándo utilizar cada mecanismo del portapapeles](../mfc/clipboard-when-to-use-each-clipboard-mechanism.md)  
  
-   [Utilizar el Portapapeles de Windows tradicional API](../mfc/clipboard-using-the-windows-clipboard.md)  
  
-   [Mediante el mecanismo OLE del portapapeles](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)  
  
-   [Copiando y pegando datos](../mfc/clipboard-copying-and-pasting-data.md)  
  
-   [Agregar otros formatos](../mfc/clipboard-adding-other-formats.md)  
  
-   [\<caps:sentence id\="tgt18" sentenceid\="1bc8aafd7da110d0b343b54cffa169d9" class\="tgtSentence"\>El Portapapeles de Windows\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/ms648709)  
  
-   [Implementar el arrastrar y colocar \(OLE\)](../mfc/drag-and-drop-ole.md)  
  
## Vea también  
 [Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)