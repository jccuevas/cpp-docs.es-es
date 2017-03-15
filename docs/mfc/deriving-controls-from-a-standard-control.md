---
title: "Derivar controles de un control est&#225;ndar | Microsoft Docs"
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
  - "controles comunes [C++], derivar de"
  - "controles [MFC], derivadas"
  - "controles derivados"
  - "controles estándar"
  - "controles estándar, derivar controles de"
  - "controles comunes de Windows [C++], derivar de"
ms.assetid: a6f84315-7007-4e0e-8576-78be81254802
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Derivar controles de un control est&#225;ndar
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Como con cualquier [CWnd](../mfc/reference/cwnd-class.md)\- clase derivada, puede modificar el comportamiento de control derivando una nueva clase de una clase de control existente.  
  
### Para crear una clase de control derivada  
  
1.  Derive la clase de una clase de control existente y reemplace opcionalmente la función miembro de **crear** de modo que proporcione los argumentos necesarios a la función de **crear** de la clase base.  
  
2.  Proporciona las funciones miembro de controladores de mensajes y las entradas de mensaje\- mapa para modificar el comportamiento de control en respuesta a los mensajes específicos de Windows.  Vea [Asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md).  
  
3.  Proporciona nuevas funciones miembro para extender la funcionalidad del control \(opcional\).  
  
 Mediante un control derivado de un cuadro de diálogo requiere trabajo adicional.  Especificar los tipos y las posiciones de controles en un cuadro de diálogo normalmente en un recurso de la diálogo\- plantilla.  Si crea una clase de control derivada, no podrá especificarlo en una plantilla de diálogo porque el compilador de recursos no sabe nada sobre la clase derivada.  
  
#### Para colocar el control derivado en un cuadro de diálogo  
  
1.  Inserte un objeto de la clase control derivada en la declaración de la clase derivada del diálogo.  
  
2.  Reemplace la función miembro de `OnInitDialog` en la clase de diálogo para llamar a la función miembro de `SubclassDlgItem` para el control derivado.  
  
 `SubclassDlgItem` “crea una subclase dinámicamente” un control creado a partir de una plantilla de cuadro de diálogo.  Cuando se crea un control subclases dinámicamente, el enlace en Windows, procesa algunos mensajes dentro de dispone de la aplicación, pasa los restantes mensajes en Windows.  Para obtener más información, vea la función miembro de [SubclassDlgItem](../Topic/CWnd::SubclassDlgItem.md) de la clase `CWnd` en *la referencia de MFC*.  El ejemplo siguiente se muestra cómo se puede escribir un reemplazo de `OnInitDialog` para llamar a `SubclassDlgItem`:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#3](../mfc/codesnippet/CPP/deriving-controls-from-a-standard-control_1.cpp)]  
  
 Dado que el control derivado se inserta en la clase de diálogo, se construido cuando se construye el cuadro de diálogo, y se destruirá cuando se destruye el cuadro de diálogo.  Compare este código de ejemplo en [Agregar Controles a mano](../mfc/adding-controls-by-hand.md).  
  
## Vea también  
 [Crear y usar controles](../mfc/making-and-using-controls.md)   
 [Controles](../mfc/controls-mfc.md)