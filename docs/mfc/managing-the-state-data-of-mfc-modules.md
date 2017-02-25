---
title: "Administrar los datos de estado de los m&#243;dulos MFC | Microsoft Docs"
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
  - "administración de datos [C++]"
  - "administración de datos [C++], módulos MFC"
  - "interfaces exportada y estado global [C+]"
  - "estado global [C++]"
  - "MFC [C++], administrar datos de estado"
  - "estado del módulo restaurado"
  - "estados de módulos, guardar y restaurar"
  - "módulos múltiples"
  - "puntos de entrada de procedimiento de ventana [C++]"
ms.assetid: 81889c11-0101-4a66-ab3c-f81cf199e1bb
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Administrar los datos de estado de los m&#243;dulos MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se abordan los datos de estado de los módulos MFC y cómo actualizan a este estado cuando el flujo de ejecución \(el código de ruta toma con una aplicación en ejecución\) entra y sale de un módulo.  Describen los estados de módulos de conmutación con macros de `AFX_MANAGE_STATE` y de `METHOD_PROLOGUE` también.  
  
> [!NOTE]
>  El término “módulo” aquí hace referencia a un programa ejecutable, o a un archivo DLL \(o conjunto de archivos DLL\) que funciona independientemente del resto de la aplicación, pero usa una copia compartida de MFC DLL.  Un control ActiveX es un ejemplo típico de un módulo.  
  
 Como se muestra en la ilustración siguiente, MFC tiene datos de estado para cada módulo utilizado en una aplicación.  Los ejemplos de estos datos incluyen los identificadores de instancia de Windows \(utilizados para cargar recursos\), punteros a `CWinApp` y los objetos actuales de `CWinThread` de una aplicación, los recuentos de OLE de referencia de módulo, y una variedad de mapas que mantener las conexiones entre los controladores de objeto de Windows y las instancias correspondientes de objetos MFC.  Sin embargo, cuando una aplicación utiliza varios módulos, los datos de estado de cada módulo no es una de ancho.  En su lugar, cada módulo tiene su propia copia privada de los datos de estado de MFC.  
  
 ![Datos de estado de un solo módulo &#40;aplicación&#41;](../mfc/media/vc387n1.png "vc387N1")  
Datos de estado de un solo módulo \(aplicación\)  
  
 Los datos de estado de un módulo se contiene en una estructura y siempre está disponible a través de un puntero a esa estructura.  Cuando el flujo de ejecución escribe un módulo determinado, como se muestra en la ilustración siguiente, que el estado del módulo debe ser “actual” o estado “real”.  Por consiguiente, cada objeto de subproceso tiene un puntero a la estructura eficaz del estado de esa aplicación.  Conservar este puntero actualizado siempre es vital para administrar el estado global de la aplicación y mantener la integridad del estado de cada módulo.  Administración incorrecta de estado global puede causar un comportamiento de aplicación imprevisible.  
  
 ![Datos de estado de varios módulos](../mfc/media/vc387n2.png "vc387N2")  
Datos de estado de varios módulos  
  
 Es decir cada módulo es responsable correctamente de cambiar entre estados de módulos en absoluto de los puntos de entrada.  Un “punto de entrada” es cualquier lugar donde el flujo de ejecución puede escribir el código del módulo.  Entre los puntos de entrada:  
  
-   [Funciones exportadas de un archivo DLL](../mfc/exported-dll-function-entry-points.md)  
  
-   [Funciones miembro de interfaces COM](../mfc/com-interface-entry-points.md)  
  
-   [Procedimientos de ventana](../mfc/window-procedure-entry-points.md)  
  
## Vea también  
 [Temas generales de MFC](../mfc/general-mfc-topics.md)