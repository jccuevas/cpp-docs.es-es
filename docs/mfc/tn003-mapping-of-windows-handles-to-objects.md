---
title: 'TN003: Asignar Windows identificadores de objetos | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mapping
dev_langs:
- C++
helpviewer_keywords:
- TN003
- handle maps
- Windows handles to objects [MFC]
- mappings [MFC], Windows handles to objects
ms.assetid: fbea9f38-992c-4091-8dbc-f29e288617d6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b022c4c42a7373f9bfc23c1fff5be2c1317709de
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43692453"
---
# <a name="tn003-mapping-of-windows-handles-to-objects"></a>TN003: Asignar identificadores de Windows a objetos
Esta nota describe las MFC rutinas que admiten la asignación de Windows objeto identificadores de objetos de C++.  
  
## <a name="the-problem"></a>El problema  
 Objetos de Windows se suelen representar por distintos [controlar](/windows/desktop/WinProg/windows-data-types) objetos clases MFC el ajustan manipuladores de objeto de Windows con los objetos de C++. El identificador de las funciones de la biblioteca de clases MFC de ajuste le permite buscar el objeto de C++ que se ajuste el objeto de Windows que tiene un identificador determinado. Sin embargo, en ocasiones, un objeto no tiene un objeto de contenedor de C++ y en estos momentos, el sistema crea un objeto temporal para que actúe como el contenedor de C++.  
  
 Los objetos de Windows que utilizan asignaciones de identificadores son los siguientes:  
  
-   HWND ([CWnd](../mfc/reference/cwnd-class.md) y `CWnd`-las clases derivadas)  
  
-   HDC ([CDC](../mfc/reference/cdc-class.md) y `CDC`-las clases derivadas)  
  
-   HMENU ([CMenu](../mfc/reference/cmenu-class.md))  
  
-   HPEN ([CGdiObject](../mfc/reference/cgdiobject-class.md))  
  
-   HBRUSH (`CGdiObject`)  
  
-   HFONT (`CGdiObject`)  
  
-   HBITMAP (`CGdiObject`)  
  
-   HPALETTE (`CGdiObject`)  
  
-   HRGN (`CGdiObject`)  
  
-   HIMAGELIST ([CImageList](../mfc/reference/cimagelist-class.md))  
  
-   SOCKET ([CSocket](../mfc/reference/csocket-class.md))  
  
 Especifica un identificador a uno de estos objetos, puede encontrar el objeto MFC que encapsula el identificador llamando al método estático `FromHandle`. Por ejemplo, dado un HWND llamado *hWnd*, la siguiente línea devolverá un puntero a la `CWnd` que ajusta *hWnd*:  
  
```  
CWnd::FromHandle(hWnd)  
```  
  
 Si *hWnd* no tiene un objeto contenedor específico, un archivo temporal `CWnd` se crea para encapsular *hWnd*. Esto permite obtener un objeto de C++ válido de cualquiera de ellos.  
  
 Una vez que un objeto contenedor, puede recuperar su identificador de una variable de miembro público de la clase contenedora. En el caso de un `CWnd`, *m_hWnd* contiene el HWND para ese objeto.  
  
## <a name="attaching-handles-to-mfc-objects"></a>Asociar controladores a los objetos MFC  
 Proporciona un objeto de contenedor de identificador recién creado y un identificador a un objeto de Windows, puede asociar las dos mediante una llamada a la `Attach` funcione como se muestra en este ejemplo:  
  
```  
CWnd myWnd;  
myWnd.Attach(hWnd);
```  
  
 Esto crea una entrada en la asociación de asignación permanente *myWnd* y *hWnd*. Una llamada a `CWnd::FromHandle(hWnd)` ahora devolverá un puntero a *myWnd*. Cuando *myWnd* es eliminado, el destructor se destruye automáticamente *hWnd* mediante una llamada a la Windows [DestroyWindow](/windows/desktop/api/winuser/nf-winuser-destroywindow) función. Si esto no es el deseado, *hWnd* se debe desasociar de *myWnd* antes *myWnd* se destruye (normalmente al salir del ámbito en el que *myWnd*se ha definido). El `Detach` método hace esto.  
  
```  
myWnd.Detach();
```  
  
## <a name="more-about-temporary-objects"></a>Más información acerca de los objetos temporales  
 Objetos temporales se crean cada vez que `FromHandle` se especifica un identificador que no tiene todavía un objeto contenedor. Estos objetos temporales se desasocian de su identificador y eliminados por el `DeleteTempMap` funciones. De forma predeterminada [CWinThread::OnIdle](../mfc/reference/cwinthread-class.md#onidle) llama automáticamente a `DeleteTempMap` para cada clase que admita asignaciones de identificadores temporales. Esto significa que no se puede suponer que un puntero a un objeto temporal serán válido más allá del punto de salir de la función donde se ha obtenido el puntero.  
  
## <a name="wrapper-objects-and-multiple-threads"></a>Objetos de contenedor y varios subprocesos  
 Objetos temporales y permanentes se mantienen en una base por subproceso. Es decir, un subproceso no puede tener acceso a objetos de contenedor de C++ de otro subproceso, independientemente de si es temporal o permanente.  
  
 Para pasar estos objetos de un subproceso a otro, siempre envíelos como su nativo `HANDLE` tipo. Pasar un objeto de contenedor de C++ desde un subproceso a otro suelen provocar resultados inesperados.  
  
## <a name="see-also"></a>Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

