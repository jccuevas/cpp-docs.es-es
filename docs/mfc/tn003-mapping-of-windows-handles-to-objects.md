---
title: "TN003: Asignar identificadores de Windows a objetos | Microsoft Docs"
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
  - "vc.mapping"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "asignaciones de identificadores"
  - "asignaciones, identificadores de Windows en objetos"
  - "TN003"
  - "identificadores de Windows en objetos [C++]"
ms.assetid: fbea9f38-992c-4091-8dbc-f29e288617d6
caps.latest.revision: 15
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN003: Asignar identificadores de Windows a objetos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Esta nota describe las rutinas de MFC que los controladores de objeto de soporte de Windows que se asignan a los objetos de C\+\+.  
  
## El problema  
 Los objetos de Windows se representan normalmente por diversos controladores de objeto de Windows de ajuste de las clases MFC de los objetos de [IDENTIFICADOR](http://msdn.microsoft.com/library/windows/desktop/aa383751) con objetos de C\+\+.  Las funciones de ajuste del identificador de la biblioteca de clases de MFC permiten encontrar el objeto de C\+\+ que está ajustando el objeto de Windows que tenga un identificador determinado.  Sin embargo, un objeto no tiene a veces objeto contenedor de c\+\+. y en estas horas el sistema crea un objeto temporal para que actúe como contenedor de C\+\+.  
  
 Los objetos de Windows que son los mapas del identificador de uso como sigue:  
  
-   HWND \([CWnd](../mfc/reference/cwnd-class.md) y `CWnd`\- clases derivadas\)  
  
-   HDC \([CDC](../mfc/reference/cdc-class.md) y `CDC`\- clases derivadas\)  
  
-   HMENU \([CMenu](../mfc/reference/cmenu-class.md)\)  
  
-   HPEN \([CGdiObject](../mfc/reference/cgdiobject-class.md)\)  
  
-   HBRUSH \(`CGdiObject`\)  
  
-   HFONT \(`CGdiObject`\)  
  
-   HBITMAP \(`CGdiObject`\)  
  
-   HPALETTE \(`CGdiObject`\)  
  
-   HRGN \(`CGdiObject`\)  
  
-   HIMAGELIST \([CImageList](../mfc/reference/cimagelist-class.md)\)  
  
-   SOCKET \([CSocket](../mfc/reference/csocket-class.md)\)  
  
 Dado un identificador de estos objetos, puede encontrar el objeto de MFC que contiene el identificador llamando al método estático `FromHandle`.  Por ejemplo, dado un HWND denominado `hWnd`, la línea siguiente devolverá un puntero a `CWnd` que contiene `hWnd`:  
  
```  
CWnd::FromHandle(hWnd)  
```  
  
 Si `hWnd` no tiene un objeto específico del contenedor, `CWnd` temporal se crea para ajustar `hWnd`.  Esto permite obtener un objeto de C\+\+ válido de cualquier identificador.  
  
 Después de tener un objeto contenedor, puede recuperar el identificador de una variable miembro public de la clase contenedora.  En el caso de `CWnd`, `m_hWnd` contiene el HWND para ese objeto.  
  
## Asociar los controladores a objetos MFC  
 Dado un objeto creado recientemente de identificador\- contenedor y un identificador de un objeto de Windows, puede asociar los dos llamando a la función de `Attach` como en este ejemplo:  
  
```  
CWnd myWnd;  
myWnd.Attach(hWnd);  
```  
  
 Esto crea una entrada en el mapa permanente que asocia `myWnd` y `hWnd`.  La llamada `CWnd::FromHandle(hWnd)` ahora devolverá un puntero a `myWnd`.  Cuando se elimina `myWnd` , destructor automáticamente destruirá `hWnd` llamando a la función de Windows [DestroyWindow](http://msdn.microsoft.com/library/windows/desktop/ms632682) .  Si no se desea, `hWnd` se debe desasociar de `myWnd` antes de que se destruya `myWnd` normalmente al dejar el ámbito en el que `myWnd` se definió\).  El método de `Detach` hace.  
  
```  
myWnd.Detach();  
```  
  
## Más información sobre objetos temporales  
 Se crean los objetos temporales siempre que `FromHandle` se indique un identificador que aún no tiene un objeto contenedor.  Estos objetos temporales se desasocian del identificador y eliminado por `DeleteTempMap` funciona.  De forma predeterminada [CWinThread::OnIdle](../Topic/CWinThread::OnIdle.md) llama automáticamente a `DeleteTempMap` para cada clase que admita mapas temporales ID.  Esto significa que no puede suponer que un puntero a un objeto temporal será válido más allá del punto de la salida de la función donde el puntero se recopilaron.  
  
## Objetos del contenedor y de Varias  
 Los objetos temporales y permanentes se mantienen en una base de por\- subproceso.  Es decir, un subproceso no puede tener acceso a los objetos del contenedor de C\+\+ de otro subproceso, independientemente de si es temporal o permanente.  
  
 Para pasar estos objetos a partir de un subproceso a otro, envíelos siempre como tipo nativo de `HANDLE` .  Pasar el objeto contenedor de c\+\+. a partir de un subproceso a otro producirá a menudo resultados inesperados.  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)