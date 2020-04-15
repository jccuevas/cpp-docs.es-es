---
title: 'TN070: Nombres de clases de ventana'
ms.date: 11/04/2016
helpviewer_keywords:
- window class names [MFC]
- TN070 [MFC]
ms.assetid: 90617912-dd58-4a7c-9082-ced71736d7cd
ms.openlocfilehash: ad43f5af5d2e90cb5fc2bc90f0909c2b495b4a4c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373482"
---
# <a name="tn070-mfc-window-class-names"></a>TN070: Nombres de clases de ventana

> [!NOTE]
> La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

Las ventanas MFC usan un nombre de clase creado dinámicamente que refleja las características de la ventana. MFC genera nombres de clase dinámicamente para ventanas de marco, vistas y ventanas emergentes generadas por la aplicación. Los cuadros de diálogo y controles generados por una aplicación MFC tienen el nombre proporcionado por Windows para la clase de ventana en cuestión.

Puede reemplazar el nombre de clase proporcionado dinámicamente registrando su propia clase de ventana y utilizándola en una invalidación de [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow). Sus nombres de clase proporcionados por MFC se ajustan a una de las dos formas siguientes:

```
Afx:%x:%x
Afx:%x:%x:%x:%x:%x
```

Los dígitos hexadecimales `%x` que reemplazan los caracteres se rellenan a partir de los datos de la estructura [WNDCLASS.](/windows/win32/api/winuser/ns-winuser-wndclassw) MFC usa esta técnica para que varias clases C++ que requieren estructuras **WNDCLASS** idénticas puedan compartir la misma clase de ventana registrada. A diferencia de la mayoría de las aplicaciones Win32 simples, las aplicaciones MFC tienen solo un **WNDPROC,** por lo que puede compartir fácilmente estructuras **WNDCLASS** para ahorrar tiempo y memoria. Los valores reemplazables `%x` para los caracteres mostrados anteriormente son los siguientes:

- **WNDCLASS.hInstance**

- **WNDCLASS.style**

- **WNDCLASS.hCursor**

- **WNDCLASS.hbrBackground**

- **WNDCLASS.hIcon**

El primer`Afx:%x:%x`formulario ( ) se utiliza cuando **hCursor**, **hbrBackground**y **hIcon** son todos **NULL**.

## <a name="see-also"></a>Consulte también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)<br/>
[TN020: Convenciones de nomenclatura y numeración de identificadores](../mfc/tn020-id-naming-and-numbering-conventions.md)
