---
title: 'TN017: Destruir objetos Window'
ms.date: 11/04/2016
f1_keywords:
- vc.objects
helpviewer_keywords:
- destroying windows
- TN017
- PostNcDestroy method [MFC]
ms.assetid: 5bf208a5-5683-439b-92a1-547c5ded26cd
ms.openlocfilehash: 9e52112bed0f583a3f5652f9213bd5049d543a80
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306160"
---
# <a name="tn017-destroying-window-objects"></a>TN017: Destruir objetos Window

Esta nota describe el uso de la [CWnd::PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy) método. Utilice este método si desea realizar una asignación personalizada de `CWnd`-objetos derivados. Esta nota también explica por qué debería usar [CWnd:: DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow) para destruir un objeto de Windows de C++ en lugar de la **eliminar** operador.

Si sigue las instrucciones de este tema, tendrá pocos problemas de limpieza. Estos problemas pueden originarse problemas como si se olvida de eliminar o liberar memoria de C++, si se olvida de liberar recursos del sistema, como `HWND`s o liberar objetos demasiadas veces.

## <a name="the-problem"></a>El problema

Cada objeto de windows (objeto de una clase derivada de `CWnd`) representa un objeto de C++ y un `HWND`. Los objetos de C++ se asignan en el montón de la aplicación y `HWND`s se asignan los recursos del sistema mediante el Administrador de ventanas. Dado que hay varias maneras para destruir un objeto de ventana, que debemos proporcionar un conjunto de reglas que impiden que el sistema las pérdidas de memoria o recursos. Estas reglas también deben evitar que los objetos e identificadores de Windows impiden la destrucción más de una vez.

## <a name="destroying-windows"></a>Destruir Windows

Éstas son las dos opciones permitidas para destruir un objeto de Windows:

- Una llamada a `CWnd::DestroyWindow` o la API de Windows `DestroyWindow`.

- Eliminar de forma explícita con el **eliminar** operador.

El primer caso es la más común. En este caso se aplica incluso si el código no llama a `DestroyWindow` directamente. Cuando directamente, el usuario cierra una ventana de marco, esta acción genera el mensaje WM_CLOSE y la respuesta predeterminada a este mensaje es llamar a `DestroyWindow.` cuando se destruye una ventana primaria, se llama Windows `DestroyWindow` para todos sus elementos secundarios.

El segundo caso, el uso de la **eliminar** operador en objetos de Windows, debe ser poco frecuentes. Las siguientes son algunos casos donde se usan **eliminar** es la opción correcta.

## <a name="auto-cleanup-with-cwndpostncdestroy"></a>Limpieza automática de CWnd::PostNcDestroy

Cuando el sistema destruye una ventana de Windows, el último mensaje de Windows que se envían a la ventana es WM_NCDESTROY. El valor predeterminado `CWnd` es el controlador para ese mensaje [CWnd::OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy). `OnNcDestroy` se desasociará del `HWND` desde C++ objeto y llamar a la función virtual `PostNcDestroy`. Algunas clases reemplazar esta función para eliminar el objeto de C++.

La implementación predeterminada de `CWnd::PostNcDestroy` no hace nada, lo que es adecuado para los objetos de ventana que se asignan en el marco de pila o incrustados en otros objetos. Esto no es apropiado para los objetos de ventana que están diseñados para que se asignan en el montón sin ningún otro objeto. En otras palabras, no es adecuado para los objetos de ventana que no se incrustan en los demás objetos de C++.

Invalidan las clases que están diseñadas para ser asignado por sí solo en el montón el `PostNcDestroy` método para realizar un **eliminar este**. Esta instrucción liberará memoria asociado al objeto de C++. Aunque el valor predeterminado `CWnd` llamadas de destructor `DestroyWindow` si *m_hWnd* es distinto de NULL, esto no provocar una recursividad infinita porque el identificador será NULL y desasociadas durante la fase de limpieza.

> [!NOTE]
>  El sistema llama normalmente `CWnd::PostNcDestroy` después de procesar el mensaje WM_NCDESTROY de Windows y la `HWND` y C++ ya no está conectado el objeto de ventana. El sistema también llamará a `CWnd::PostNcDestroy` en la implementación de la mayoría [CWnd:: Create](../mfc/reference/cwnd-class.md#create) llama si se produce un error. Las reglas de limpieza automática se describen más adelante en este tema.

## <a name="auto-cleanup-classes"></a>Clases de limpieza automática

Las siguientes clases no están diseñadas para la limpieza automática. Normalmente, se incrustan en los demás objetos de C++ o en la pila:

- Todos los controles de Windows estándares (`CStatic`, `CEdit`, `CListBox`, y así sucesivamente).

- Las ventanas secundarias se derivan directamente de `CWnd` (por ejemplo, controles personalizados).

- Ventanas divisoras (`CSplitterWnd`).

- Barras de control de predeterminado (las clases derivadas de `CControlBar`, consulte [Nota técnica 31](../mfc/tn031-control-bars.md) para habilitar la eliminación automática para los objetos de la barra de control).

- Los cuadros de diálogo (`CDialog`) diseñado para los cuadros de diálogo modales en el marco de pila.

- El estándar de todos los cuadros de diálogo excepto `CFindReplaceDialog`.

- Los cuadros de diálogo predeterminado creados por el Asistente para clases.

Las siguientes clases están diseñadas para la limpieza automática. Normalmente, se asignan por sí mismos en el montón:

- Ventanas de marco principal (deriva directa o indirectamente `CFrameWnd`).

- Ver windows (deriva directa o indirectamente `CView`).

Si desea interrumpir estas reglas, debe invalidar el `PostNcDestroy` método en la clase derivada. Para agregar la limpieza automática a la clase, llame a su clase base y, a continuación, hacer un **eliminar este**. Para quitar la limpieza automática de la clase, llame a `CWnd::PostNcDestroy` directamente en lugar de la `PostNcDestroy` método de la clase base directa.

El uso más común de cambiar el comportamiento automático cleanup consiste en crear un cuadro de diálogo no modal que se puede asignar en el montón.

## <a name="when-to-call-delete"></a>Cuando a la llamada delete

Se recomienda que llame a `DestroyWindow` para destruir un objeto de Windows, el método de C++ o global `DestroyWindow` API.

No llame a la información global `DestroyWindow` API para destruir una ventana secundaria MDI. Debe utilizar el método virtual `CWnd::DestroyWindow` en su lugar.

Para que no realice la limpieza automática de objetos de ventana de C++, pero utiliza el **eliminar** operador puede provocar una pérdida de memoria cuando se intenta llamar a `DestroyWindow` en el `CWnd::~CWnd` destructor si VTBL no apunta a la clase derivada correctamente. Esto ocurre porque el sistema no encuentra que destruir (método) para llamar a la correspondiente. Uso de `DestroyWindow` en lugar de **eliminar** evita estos problemas. Dado que esto puede ser un error sutil, compilar en modo de depuración generará la advertencia siguiente si está en peligro.

```
Warning: calling DestroyWindow in CWnd::~CWnd
    OnDestroy or PostNcDestroy in derived class will not be called
```

En el caso de los objetos de Windows de C++ que realice la limpieza automática, se debe llamar a `DestroyWindow`. Si usas el **eliminar** operador directamente, el asignador de memoria para diagnósticos de MFC le notificará que se libere memoria dos veces. Las dos repeticiones son la primera llamada explícita y la llamada indirecta a **eliminar este** en la implementación de la limpieza automática de `PostNcDestroy`.

Después de llamar a `DestroyWindow` en un objeto que no sean de limpieza automática, el C++ objeto aún estará en torno a, pero *m_hWnd* será NULL. Después de llamar a `DestroyWindow` en un objeto de limpieza automática, el objeto de C++ habrán desaparecido, liberado por el operador delete de C++ en la implementación de la limpieza automática de `PostNcDestroy`.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
