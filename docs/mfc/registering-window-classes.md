---
title: Registrar clases de ventana | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- WndProc
dev_langs:
- C++
helpviewer_keywords:
- window classes [MFC], registering
- registry [MFC], registering classes
- AfxRegisterWndClass method [MFC]
- MFC, windows
- WinMain method [MFC], and registering window classes
- WndProc method [MFC]
- classes [MFC], registering window classes
- WinMain method [MFC]
- registering window classes [MFC]
ms.assetid: 30994bc4-a362-43da-bcc5-1bf67a3fc929
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2b2589db4d316d8421b0792e4a152e7fa390725f
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36927911"
---
# <a name="registering-window-classes"></a>Registrar clases de ventana
Ventana "classes" en la programación tradicional para Windows definen las características de una "clase" (no una clase de C++) desde que se puede crear cualquier número de windows. Este tipo de clase es una plantilla o un modelo para la creación de windows.  
  
## <a name="window-class-registration-in-traditional-programs-for-windows"></a>Registro de la clase de ventana en programas tradicionales de Windows  
 En un programa tradicional para Windows, sin MFC, procesar todos los mensajes a una ventana en su "procedimiento de ventana" o "`WndProc`." Un `WndProc` está asociado a una ventana por medio de un proceso de "registro de la clase de ventana". La ventana principal se registra en el `WinMain` función, pero las otras clases de windows pueden registrar en cualquier parte de la aplicación. Registro depende de una estructura que contiene un puntero a la `WndProc` función junto con las especificaciones para el cursor, pincel de fondo y así sucesivamente. La estructura se pasa como un parámetro, junto con el nombre de cadena de la clase, en una llamada anterior a la `RegisterClass` (función). Por lo tanto, una clase de registro puede compartirse entre varias ventanas.  
  
## <a name="window-class-registration-in-mfc-programs"></a>Registro de la clase de ventana en programas MFC  
 En cambio, la mayoría actividad de registro de clase de ventana se realiza automáticamente en un programa de marco de trabajo MFC. Si está utilizando MFC, normalmente derivar una clase de ventana de C++ de una clase de biblioteca existente utilizando la sintaxis de C++ normal para la herencia de clases. El marco de trabajo sigue utilizando tradicional "clases de registro" y proporciona varios las estándares, registradas cuando sea necesario. Puede registrar clases de registro adicionales mediante una llamada a la [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass) función global y, a continuación, pasar la clase registrada para la `Create` función miembro de `CWnd`. Como se describe aquí, tradicional es "clase de registro" en Windows no se deben confundir con una clase de C++.  
  
 Para obtener más información, consulte [Nota técnica 1](../mfc/tn001-window-class-registration.md).  
  
## <a name="see-also"></a>Vea también  
 [Creación de ventanas](../mfc/creating-windows.md)

