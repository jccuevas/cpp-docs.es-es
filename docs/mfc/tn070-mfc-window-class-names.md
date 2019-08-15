---
title: 'TN070: Nombres de clase de ventana de MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- window class names [MFC]
- TN070 [MFC]
ms.assetid: 90617912-dd58-4a7c-9082-ced71736d7cd
ms.openlocfilehash: 1d9b5de07bcc2545df6294557d1ac9f9d29e856c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513353"
---
# <a name="tn070-mfc-window-class-names"></a>TN070: Nombres de clase de ventana de MFC

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

Las ventanas de MFC utilizan un nombre de clase creado dinámicamente que refleja las características de la ventana. MFC genera nombres de clase de forma dinámica para ventanas de marco, vistas y ventanas emergentes generadas por la aplicación. Los cuadros de diálogo y controles generados por una aplicación MFC tienen el nombre proporcionado por Windows para la clase de ventana en cuestión.

Puede reemplazar el nombre de clase proporcionado dinámicamente registrando su propia clase de ventana y usando en una invalidación de [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow). Los nombres de clase proporcionados por MFC se ajustan a uno de los dos formatos siguientes:

```
Afx:%x:%x
Afx:%x:%x:%x:%x:%x
```

Los dígitos hexadecimales que reemplazan a los `%x` caracteres se rellenan a partir de los datos de la estructura [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw) . MFC usa esta técnica para que varias C++ clases que requieren estructuras **WNDCLASS** idénticas puedan compartir la misma clase de ventana registrada. A diferencia de la mayoría de las aplicaciones Win32 sencillas, las aplicaciones MFC solo tienen un **WndProc**, por lo que puede compartir fácilmente las estructuras **WNDCLASS** para ahorrar tiempo y memoria. Los valores reemplazables para los `%x` caracteres mostrados anteriormente son los siguientes:

- **WNDCLASS.hInstance**

- **WNDCLASS.style**

- **WNDCLASS.hCursor**

- **WNDCLASS.hbrBackground**

- **WNDCLASS.hIcon**

La primera forma (`Afx:%x:%x`) se usa cuando **hCursor**, **hbrBackground**y **hIcon** son todas **nulas**.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)<br/>
[TN020: Convenciones de nomenclatura y numeración de identificadores](../mfc/tn020-id-naming-and-numbering-conventions.md)
