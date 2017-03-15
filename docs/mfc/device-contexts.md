---
title: "Contextos de dispositivo | Microsoft Docs"
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
  - "BeginPaint (método), CPaintDC"
  - "CClientDC (clase), y método GetDC"
  - "CClientDC (clase), y método ReleaseDC"
  - "CDC (clase), objetos"
  - "áreas cliente"
  - "áreas cliente, y contexto de dispositivo"
  - "CMetaFileDC (clase), y método OnPrepareDC"
  - "CPaintDC (clase), contexto de dispositivo para dibujar"
  - "contextos de dispositivo [C++]"
  - "contextos de dispositivo [C++], acerca de contextos de dispositivo"
  - "contextos de dispositivo [C++], CDC (clase)"
  - "dibujos independientes de dispositivo"
  - "dibujar, contexto de dispositivo"
  - "dibujar, directamente en ventanas"
  - "dibujar, en el mouse y contextos de dispositivo"
  - "EndPaint (método)"
  - "ventanas de marco [C++], contextos de dispositivo"
  - "objetos GDI [C++], contextos de dispositivo"
  - "GetDC (método) y CClientDC (clase)"
  - "objetos gráficos, contextos de dispositivo"
  - "metarchivos y contextos de dispositivo"
  - "mouse [C++], dibujo y contextos de dispositivo"
  - "OnPrepareDC (método)"
  - "dibujar y contexto de dispositivo"
  - "impresoras [C++], contextos de dispositivo"
  - "ReleaseDC (método)"
  - "interfaz de usuario [C++], contextos de dispositivo"
  - "ventanas [C++], y contexto de dispositivo"
  - "ventanas [C++], dibujo directamente en"
ms.assetid: d0cd51f1-f778-4c7e-bf50-d738d10433c7
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Contextos de dispositivo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un contexto de dispositivo es una estructura de datos de Windows que contiene información sobre los atributos del gráfico de un dispositivo como una pantalla o una impresora.  Todas las llamadas del gráfico se hace a través de un objeto de dispositivo\- contexto, que encapsula las API de Windows para líneas, formas, y dibujar texto.  Los contextos de dispositivo permiten el gráfico independiente del dispositivo en Windows.  Los contextos de dispositivo se pueden utilizar para dibujar en la pantalla, a la impresora, o a un metarchivo.  
  
 los objetos de[CPaintDC](../mfc/reference/cpaintdc-class.md) encapsulan la frase expresiones comunes de Windows, llamando a la función de `BeginPaint` , el gráfico en el contexto del dispositivo, después llamando a la función de `EndPaint` .  El constructor de `CPaintDC` llama `BeginPaint` para usted, y el destructor llama `EndPaint`.  El proceso simplificado es crear el objeto de [CDC](../mfc/reference/cdc-class.md) , dibuja, y se destruye el objeto de `CDC` .  En el marco, mucho incluso de este proceso se automatiza.  En particular, la función de `OnDraw` se pasa `CPaintDC` preparado ya \(mediante `OnPrepareDC`\), y se dibuja simplemente dentro de.  Destruya el marco y el contexto subyacente de dispositivo se libera a Windows sobre volver de la llamada a la función de `OnDraw` .  
  
 los objetos de[CClientDC](../mfc/reference/cclientdc-class.md) encapsulan ejecutar un contexto de dispositivo que representa sólo el área cliente de una ventana.  El constructor de `CClientDC` llama a la función de `GetDC` , y las llamadas del destructor la función de `ReleaseDC` .  los objetos de[CWindowDC](../mfc/reference/cwindowdc-class.md) encapsulan un contexto de dispositivo que representa la ventana completa, incluido el cuadro.  
  
 los objetos de[CMetaFileDC](../mfc/reference/cmetafiledc-class.md) encapsulan el gráfico en un metarchivo de Windows.  A diferencia de `CPaintDC` pasado a `OnDraw`, debe en este caso llamar [OnPrepareDC](../Topic/CView::OnPrepareDC.md) personalmente.  
  
## Gráfico del mouse  
 El gráfico en un programa de base — y así la mayoría del trabajo de dispositivo\- contexto — se hace en la función miembro de `OnDraw` de la vista.  Sin embargo, todavía puede utilizar objetos de dispositivo\- contexto para otros fines.  Por ejemplo, para proporcionar comentarios de seguimiento para el movimiento del mouse en una vista, debe dibujar directamente dentro de la vista sin para `OnDraw` que espera que se va a llamar.  
  
 En este caso, puede utilizar un objeto de dispositivo\- contexto de [CClientDC](../mfc/reference/cclientdc-class.md) para dibujar directamente dentro de la vista.  
  
### ¿Sobre qué desea obtener más información?  
  
-   [\<caps:sentence id\="tgt22" sentenceid\="a12b51e88715aef1e34dc9b8f4447117" class\="tgtSentence"\>Contextos de dispositivo \(definition\)\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/dd183553)  
  
-   [Dibujar en una vista](../mfc/drawing-in-a-view.md)  
  
-   [Interpretar los datos proporcionados por el usuario a través de una vista](../mfc/interpreting-user-input-through-a-view.md)  
  
-   [\<caps:sentence id\="tgt25" sentenceid\="f3dbb554cb14503827bf0ebda53953d7" class\="tgtSentence"\>Líneas y curvas\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/dd145028)  
  
-   [\<caps:sentence id\="tgt26" sentenceid\="365f749101c5eabc8b3be48de1dc3d6b" class\="tgtSentence"\>Formas rellenas\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/dd162714)  
  
-   [\<caps:sentence id\="tgt27" sentenceid\="dc86a6302992c2d9f64d0fc6a8cfef75" class\="tgtSentence"\>Fuentes y texto\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/dd144819)  
  
-   [\<caps:sentence id\="tgt28" sentenceid\="62848e3ce5804aa985513a7922ff87b2" class\="tgtSentence"\>Colors\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/dd183450)  
  
-   [\<caps:sentence id\="tgt29" sentenceid\="ee85800dfcba9a5bdf11f101e1bbadeb" class\="tgtSentence"\>Espacios de coordenadas y transformaciones\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/dd183475)  
  
## Vea también  
 [Window \(Objetos\)](../mfc/window-objects.md)