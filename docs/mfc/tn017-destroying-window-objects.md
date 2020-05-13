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
ms.openlocfilehash: 9802669468cbbba89f23b8ac127358d1fc15ec9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370421"
---
# <a name="tn017-destroying-window-objects"></a>TN017: Destruir objetos Window

Esta nota describe el uso de la [CWnd::PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy) método. Utilice este método si desea realizar `CWnd`una asignación personalizada de objetos derivados. Esta nota también explica por qué debe usar [CWnd::DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow) para destruir un C++ Windows objeto en lugar del operador **delete.**

Si sigue las directrices de este tema, tendrá pocos problemas de limpieza. Estos problemas pueden ser el resultado de problemas como olvidarse de eliminar/liberar `HWND`memoria C++, olvidarse de liberar recursos del sistema como s o liberar objetos demasiadas veces.

## <a name="the-problem"></a>El problema

Cada objeto windows (objeto de `CWnd`una clase derivada de ) representa `HWND`un objeto C++ y un objeto . Los objetos C++ se asignan `HWND`en el montón de la aplicación y el gestor de ventanas asigna los objetos C+++ en el montón de la aplicación y los s los asigna en los recursos del sistema. Dado que hay varias maneras de destruir un objeto de ventana, debemos proporcionar un conjunto de reglas que impidan pérdidas de memoria o recursos del sistema. Estas reglas también deben evitar que los objetos y los identificadores de Windows se destruyan más de una vez.

## <a name="destroying-windows"></a>Destruir Windows

Las siguientes son las dos formas permitidas de destruir un objeto de Windows:

- Llamadas `CWnd::DestroyWindow` o `DestroyWindow`la API de Windows .

- Eliminación explícita con el operador **delete.**

El primer caso es, con mucho, el más común. Este caso se aplica incluso `DestroyWindow` si el código no llama directamente. Cuando el usuario cierra directamente una ventana de marco, esta acción genera el `DestroyWindow.` mensaje WM_CLOSE y la respuesta `DestroyWindow` predeterminada a este mensaje es llamar cuando se destruye una ventana primaria, Windows llama a todos sus elementos secundarios.

El segundo caso, el uso del operador **delete** en objetos de Windows, debe ser poco frecuente. Los siguientes son algunos casos en los que el uso de **delete** es la opción correcta.

## <a name="auto-cleanup-with-cwndpostncdestroy"></a>Limpieza automática con CWnd::PostNcDestroy

Cuando el sistema destruye una ventana de Windows, el último mensaje de Windows enviado a la ventana es WM_NCDESTROY. El `CWnd` controlador predeterminado para ese mensaje es [CWnd::OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy). `OnNcDestroy`separará el `HWND` objeto C++ y llamará `PostNcDestroy`a la función virtual . Algunas clases anulan esta función para eliminar el objeto C+++ .

La implementación `CWnd::PostNcDestroy` predeterminada de no hace nada, que es adecuado para los objetos de ventana que se asignan en el marco de pila o incrustados en otros objetos. Esto no es adecuado para los objetos de ventana que están diseñados para asignarse en el montón sin ningún otro objeto. En otras palabras, no es adecuado para los objetos de ventana que no están incrustados en otros objetos C++.

Las clases que están diseñadas para `PostNcDestroy` asignarse solas en el montón invalidan el método para eliminar **este**archivo . Esta instrucción liberará cualquier memoria asociada con el objeto C++. Aunque el `CWnd` destructor `DestroyWindow` predeterminado llama si *m_hWnd* no es NULL, esto no conduce a una recursividad infinita porque el identificador se separará y NULL durante la fase de limpieza.

> [!NOTE]
> Normalmente, `CWnd::PostNcDestroy` el sistema llama después `HWND` de procesar el mensaje de WM_NCDESTROY de Windows y el objeto de ventana C++ ya no están conectados. El sistema también `CWnd::PostNcDestroy` llamará a la implementación de la mayoría de [las llamadas CWnd::Create](../mfc/reference/cwnd-class.md#create) si se produce un error. Las reglas de limpieza automática se describen más adelante en este tema.

## <a name="auto-cleanup-classes"></a>Clases de limpieza automática

Las siguientes clases no están diseñadas para la limpieza automática. Normalmente se incrustan en otros objetos C++ o en la pila:

- Todos los controles`CStatic` `CEdit`estándar `CListBox`de Windows ( , , , , etc.).

- Cualquier ventana secundaria derivada `CWnd` directamente de (por ejemplo, controles personalizados).

- Ventanas`CSplitterWnd`divisoras ( ).

- Barras de control predeterminadas `CControlBar`(clases derivadas de , consulte [Nota técnica 31](../mfc/tn031-control-bars.md) para habilitar la eliminación automática para objetos de barra de control).

- Diálogos`CDialog`( ) diseñados para cuadros de diálogo modales en el marco de pila.

- Todos los cuadros `CFindReplaceDialog`de diálogo estándar excepto .

- Los cuadros de diálogo predeterminados creados por ClassWizard.

Las siguientes clases están diseñadas para la limpieza automática. Por lo general se asignan por sí mismos en el montón:

- Ventanas de marco principal (derivadas `CFrameWnd`directa o indirectamente de ).

- Ver ventanas (derivadas directa `CView`o indirectamente de ).

Si desea interrumpir estas reglas, debe `PostNcDestroy` invalidar el método en la clase derivada. Para agregar la limpieza automática a la clase, llame a la clase base y, a continuación, elimine **este**archivo . Para quitar la limpieza automática `CWnd::PostNcDestroy` de la `PostNcDestroy` clase, llame directamente en lugar del método de la clase base directa.

El uso más común de cambiar el comportamiento de limpieza automática es crear un cuadro de diálogo no secuenciado que se puede asignar en el montón.

## <a name="when-to-call-delete"></a>Cuándo llamar a eliminar

Se recomienda llamar `DestroyWindow` para destruir un objeto de Windows, ya sea el método C++ o la API global. `DestroyWindow`

No llame a `DestroyWindow` la API global para destruir una ventana secundaria MDI. Debe usar el `CWnd::DestroyWindow` método virtual en su lugar.

Para los objetos de ventana C++ que no realizan la limpieza automática, `DestroyWindow` el `CWnd::~CWnd` uso del operador **delete** puede provocar una pérdida de memoria cuando intenta llamar al destructor si el VTBL no apunta a la clase derivada correctamente. Esto ocurre porque el sistema no puede encontrar el método de destrucción adecuado para llamar. El `DestroyWindow` uso en lugar de **eliminar** evita estos problemas. Dado que esto puede ser un error sutil, compilar en modo de depuración generará la siguiente advertencia si está en riesgo.

```
Warning: calling DestroyWindow in CWnd::~CWnd
    OnDestroy or PostNcDestroy in derived class will not be called
```

En el caso de los objetos de Windows C++ que realizan la limpieza automática, debe llamar a `DestroyWindow`. Si usa el operador **delete** directamente, el asignador de memoria de diagnóstico MFC le notificará que está liberando memoria dos veces. Las dos apariciones son su primera llamada explícita y la llamada `PostNcDestroy`indirecta para eliminar **esto** en la implementación de limpieza automática de .

Después `DestroyWindow` de llamar a un objeto que no es de limpieza automática, el objeto C++ seguirá existiendo, pero *m_hWnd* será NULL. Después `DestroyWindow` de llamar a un objeto de limpieza automática, el objeto C++ desaparecerá, liberado `PostNcDestroy`por el operador de eliminación C++ en la implementación de limpieza automática de .

## <a name="see-also"></a>Consulte también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
