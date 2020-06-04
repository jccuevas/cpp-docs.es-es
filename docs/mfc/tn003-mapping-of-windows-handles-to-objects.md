---
title: 'TN003: Asignación de identificadores de Windows a objetos'
ms.date: 11/04/2016
f1_keywords:
- vc.mapping
helpviewer_keywords:
- TN003
- handle maps
- Windows handles to objects [MFC]
- mappings [MFC], Windows handles to objects
ms.assetid: fbea9f38-992c-4091-8dbc-f29e288617d6
ms.openlocfilehash: 45492963e1b686e03eb59c320fdc3d52d1534f7d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513539"
---
# <a name="tn003-mapping-of-windows-handles-to-objects"></a>TN003: Asignación de identificadores de Windows a objetos

En esta nota se describen las rutinas de MFC que admiten la C++ asignación de identificadores de objetos de Windows a objetos.

## <a name="the-problem"></a>El problema

Los objetos de Windows normalmente se representan mediante varios objetos de [identificador](/windows/win32/WinProg/windows-data-types) . las clases MFC ajustan los identificadores de objetos de Windows con C++ objetos. Las funciones de ajuste de identificador de la biblioteca de clases MFC permiten C++ encontrar el objeto que ajusta el objeto de Windows que tiene un identificador determinado. Sin embargo, a veces un objeto no tiene C++ un objeto contenedor y, en estos momentos, el sistema crea un objeto temporal para C++ que actúe como contenedor.

Los objetos de Windows que utilizan asignaciones de identificadores son los siguientes:

- HWND (clases derivadas de[CWnd](../mfc/reference/cwnd-class.md) y `CWnd`)

- HDC (clases derivadas de[CDC](../mfc/reference/cdc-class.md) y `CDC`)

- HMENU ([CMenu](../mfc/reference/cmenu-class.md))

- HPEN ([CGdiObject](../mfc/reference/cgdiobject-class.md))

- HBRUSH (`CGdiObject`)

- HFONT (`CGdiObject`)

- HBITMAP (`CGdiObject`)

- HPALETTE (`CGdiObject`)

- HRGN (`CGdiObject`)

- HIMAGELIST ([CImageList](../mfc/reference/cimagelist-class.md))

- SOCKET ([CSocket](../mfc/reference/csocket-class.md))

Dado un identificador a cualquiera de estos objetos, puede encontrar el objeto MFC que ajusta el identificador llamando al método `FromHandle`estático. Por ejemplo, dado un HWND denominado *hWnd*, la línea siguiente devolverá un puntero a `CWnd` que contiene *hWnd*:

```
CWnd::FromHandle(hWnd)
```

Si *hWnd* no tiene un objeto contenedor específico, se crea un `CWnd` temporal para ajustar *hWnd*. Esto permite obtener un objeto válido C++ de cualquier controlador.

Una vez que tenga un objeto contenedor, puede recuperar su identificador de una variable de miembro público de la clase contenedora. En el caso de `CWnd`, *m_hWnd* contiene el HWND para ese objeto.

## <a name="attaching-handles-to-mfc-objects"></a>Adjuntar controladores a objetos MFC

Dado un objeto Handle-wrapper recién creado y un identificador a un objeto de Windows, puede asociar los dos llamando a `Attach` la función como en este ejemplo:

```
CWnd myWnd;
myWnd.Attach(hWnd);
```

Esto crea una entrada en el mapa permanente que asocia *myWnd* y *hWnd*. Llamar `CWnd::FromHandle(hWnd)` a devolverá ahora un puntero a *myWnd*. Cuando se elimina *myWnd* , el destructor destruye automáticamente *hWnd* mediante una llamada a la función [DestroyWindow](/windows/win32/api/winuser/nf-winuser-destroywindow) de Windows. Si no se desea, *hWnd* debe desasociarse de *myWnd* antes de que *myWnd* se destruya (normalmente al mantener el ámbito en el que se definió *myWnd* ). El `Detach` método lo hace.

```
myWnd.Detach();
```

## <a name="more-about-temporary-objects"></a>Más información sobre los objetos temporales

Los objetos temporales se crean `FromHandle` siempre que se proporciona un identificador que aún no tiene un objeto contenedor. Estos objetos temporales se desasocian de su identificador y se eliminan de las `DeleteTempMap` funciones. De forma predeterminada, [CWinThread:: OnIdle](../mfc/reference/cwinthread-class.md#onidle) llama `DeleteTempMap` automáticamente a cada clase que admita asignaciones de identificadores temporales. Esto significa que no se puede asumir que un puntero a un objeto temporal será válido más allá del punto de salida de la función en la que se obtuvo el puntero.

## <a name="wrapper-objects-and-multiple-threads"></a>Objetos contenedor y varios subprocesos

Tanto los objetos temporales como los permanentes se mantienen por subproceso. Es decir, un subproceso no puede tener acceso C++ a los objetos contenedores de otro subproceso, independientemente de si es temporal o permanente.

Para pasar estos objetos de un subproceso a otro, envíelos siempre como su `HANDLE` tipo nativo. Pasar un C++ objeto contenedor de un subproceso a otro suele producir resultados inesperados.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
