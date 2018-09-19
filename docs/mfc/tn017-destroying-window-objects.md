---
title: 'TN017: Destruir objetos Window | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.objects
dev_langs:
- C++
helpviewer_keywords:
- destroying windows
- TN017
- PostNcDestroy method [MFC]
ms.assetid: 5bf208a5-5683-439b-92a1-547c5ded26cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fd7b8e9882d682d3e7a9b9162f1f2f84675cd590
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36951538"
---
# <a name="tn017-destroying-window-objects"></a>TN017: Destruir objetos Window
Esta nota describe el uso de la [CWnd::PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy) método. Utilice este método si desea realizar una asignación personalizada de `CWnd`-objetos derivados. Esta nota también explica por qué debe usar [CWnd:: DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow) para destruir un objeto de Windows de C++ en lugar de la **eliminar** operador.  
  
 Si sigue las instrucciones de este tema, tendrá pocos problemas de limpieza. Estos problemas pueden deberse a problemas, como olvidar delete/liberar memoria de C++, olvidar liberar recursos del sistema como `HWND`s o liberar objetos demasiadas veces.  
  
## <a name="the-problem"></a>El problema  
 Cada objeto de windows (objeto de una clase derivada de `CWnd`) representa un objeto de C++ y un `HWND`. Objetos de C++ se asignan en el montón de la aplicación y `HWND`s se asignan en recursos del sistema mediante el Administrador de ventanas. Dado que hay varias maneras para destruir un objeto de ventana, debemos proporcionar un conjunto de reglas que impidan el sistema pérdidas de recursos o memoria. Estas reglas también deben evitar que objetos e identificadores de Windows desde la que se está destruyendo más de una vez.  
  
## <a name="destroying-windows"></a>Destruir ventanas  
 Éstas son las dos maneras permitidas para destruir un objeto de Windows:  
  
-   Al llamar a `CWnd::DestroyWindow` o la API de Windows `DestroyWindow`.  
  
-   Eliminar de forma explícita con la **eliminar** operador.  
  
 El primer caso es el más común. En este caso se aplica incluso si el código no llama a `DestroyWindow` directamente. Cuando el usuario cierra directamente una ventana de marco, esta acción genera el mensaje WM_CLOSE y la respuesta predeterminada a este mensaje es llamar a `DestroyWindow.` cuando se destruye una ventana primaria, Windows llama `DestroyWindow` para todos sus elementos secundarios.  
  
 El segundo caso, el uso de la **eliminar** operador en objetos de Windows, debe ser infrecuentes. Las siguientes son algunos de los casos, cuando usa **eliminar** es la opción correcta.  
  
## <a name="auto-cleanup-with-cwndpostncdestroy"></a>Limpieza automática de CWnd::PostNcDestroy  
 Cuando el sistema destruye una ventana de Windows, el último mensaje de Windows que se envían a la ventana es WM_NCDESTROY. El valor predeterminado `CWnd` controlador para que el mensaje es [CWnd::OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy). `OnNcDestroy` se desasociará la `HWND` de C++ de objetos y llamar a la función virtual `PostNcDestroy`. Algunas clases invalidan esta función para eliminar el objeto de C++.  
  
 La implementación predeterminada de `CWnd::PostNcDestroy` no hace nada, lo que es adecuado para los objetos de ventana que se asignan en el marco de pila o incrustados en otros objetos. Esto no es adecuado para los objetos de ventana que se han diseñado para que se asignan en el montón sin ningún otro objeto. En otras palabras, no es adecuado para los objetos de ventana que no se incrustan en otros objetos de C++.  
  
 Esas clases que están diseñadas para asignarse por sí solo en el montón de invalidación el `PostNcDestroy` método para realizar un **eliminar este**. Esta instrucción liberará memoria asociado con el objeto de C++. Aunque el valor predeterminado `CWnd` llamadas de destructor `DestroyWindow` si *m_hWnd* es distinto de NULL, esto no da lugar a una recursión infinita porque el identificador será desasociado y NULL durante la fase de limpieza.  
  
> [!NOTE]
>  El sistema llama normalmente `CWnd::PostNcDestroy` después de procesar el mensaje WM_NCDESTROY de Windows y el `HWND` y el objeto de ventana de C++ ya no están conectados. El sistema también llamará `CWnd::PostNcDestroy` en la implementación de la mayoría [CWnd:: Create](../mfc/reference/cwnd-class.md#create) llama si se produce el error. Las reglas de limpieza automática se describen más adelante en este tema.  
  
## <a name="auto-cleanup-classes"></a>Clases de limpieza automática  
 Las siguientes clases no están diseñadas para la limpieza automática. Normalmente están incrustados en otros objetos de C++ o en la pila:  
  
-   Todos los controles estándar de Windows (`CStatic`, `CEdit`, `CListBox`, y así sucesivamente).  
  
-   Las ventanas secundarias se derivan directamente de `CWnd` (por ejemplo, los controles personalizados).  
  
-   Ventanas divisoras (`CSplitterWnd`).  
  
-   Barras de control de predeterminado (las clases derivadas de `CControlBar`, consulte [Nota técnica 31](../mfc/tn031-control-bars.md) para habilitar la eliminación automática para los objetos de la barra de control).  
  
-   Los cuadros de diálogo (`CDialog`) diseñado para los cuadros de diálogo modales en el marco de pila.  
  
-   El estándar de todos los cuadros de diálogo excepto `CFindReplaceDialog`.  
  
-   Los cuadros de diálogo predeterminado creados por el asistente.  
  
 Las siguientes clases están diseñadas para la limpieza automática. Normalmente, se asignan por sí solas o en el montón:  
  
-   Ventanas de marco principal (derivan directa o indirectamente `CFrameWnd`).  
  
-   Ver las ventanas (derivan directa o indirectamente `CView`).  
  
 Si desea interrumpir estas reglas, se debe invalidar el `PostNcDestroy` método en su clase derivada. Para agregar la limpieza automática a la clase, llame a su clase base y, a continuación, realice una **eliminar este**. Para quitar la limpieza automática de la clase, llame a `CWnd::PostNcDestroy` directamente en lugar de la `PostNcDestroy` método de la clase base directa.  
  
 El uso más común de cambiar el comportamiento de limpieza automática consiste en crear un cuadro de diálogo no modal que se pueden asignar en el montón.  
  
## <a name="when-to-call-delete"></a>En la llamada delete  
 Se recomienda llamar a `DestroyWindow` para destruir un objeto de Windows, el método de C++ o global `DestroyWindow` API.  
  
 No llame a la información global `DestroyWindow` API para destruir una ventana secundaria MDI. Debe utilizar el método virtual `CWnd::DestroyWindow` en su lugar.  
  
 Para que no realice la limpieza automática de objetos de ventana de C++, pero utiliza el **eliminar** operador puede provocar una pérdida de memoria cuando se intenta llamar a `DestroyWindow` en el `CWnd::~CWnd` destructor si VTBL no apunta a la clase derivada correctamente. Esto ocurre porque el sistema no encuentra que la correspondiente destroy (método) para llamar a. Usar `DestroyWindow` en lugar de **eliminar** evita estos problemas. Compilar en modo de depuración porque esto puede ser un error sutil, se generará la advertencia siguiente si están en riesgo.  
  
```  
Warning: calling DestroyWindow in CWnd::~CWnd  
    OnDestroy or PostNcDestroy in derived class will not be called  
```  
  
 En el caso de objetos de Windows de C++ que realice la limpieza automática, se debe llamar a `DestroyWindow`. Si usas el **eliminar** operador directamente, el asignador de memoria para diagnósticos de MFC le notificará que se libere memoria dos veces. Las dos apariciones son la primera llamada explícita y las llamadas indirectas a **eliminar este** en la implementación de la limpieza automática de `PostNcDestroy`.  
  
 Después de llamar a `DestroyWindow` en un objeto no-limpieza automática, el objeto de C++ se seguirá alrededor, pero *m_hWnd* será NULL. Después de llamar a `DestroyWindow` en un objeto de la limpieza automática, el objeto de C++ se habrán eliminado, libere el operador delete de C++ en la implementación de la limpieza automática de `PostNcDestroy`.  
  
## <a name="see-also"></a>Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

