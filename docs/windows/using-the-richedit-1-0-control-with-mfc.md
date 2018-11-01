---
title: Utilizar el control RichEdit 1.0 con MFC
ms.date: 11/04/2016
helpviewer_keywords:
- RichEdit 1.0 control
- rich edit controls [C++], RichEdit 1.0
ms.assetid: 5a9060dd-44d8-4ef3-956e-16152f7e23d2
ms.openlocfilehash: 080ad995b9c7a041337d9b296d6ef8906e7f20ec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468320"
---
# <a name="using-the-richedit-10-control-with-mfc"></a>Utilizar el control RichEdit 1.0 con MFC

Para utilizar un control RichEdit, primero debe llamar a [AfxInitRichEdit2](../mfc/reference/application-information-and-management.md#afxinitrichedit2) para cargar el Control RichEdit 2.0 (RICHED20. Archivo DLL), o llamar a [AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit) para cargar el Control RichEdit 1.0 anterior (RICHED32. (DLL).

Puede usar actual [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) clase con el control RichEdit 1.0 anterior, pero `CRichEditCtrl` sólo está diseñada para admitir el control RichEdit 2.0. Dado que RichEdit 1.0 y RichEdit 2.0 son muy similares, funcionará la mayoría de los métodos; Sin embargo, observe que hay algunas diferencias entre los controles 1.0 y 2.0, por lo que algunos métodos podrían no funcionen correctamente o no funcionará en absoluto.

## <a name="requirements"></a>Requisitos

MFC

## <a name="see-also"></a>Vea también

[Solucionar problemas del Editor de cuadros de diálogo](../windows/troubleshooting-the-dialog-editor.md)<br/>
[Editor de cuadros de diálogo](../windows/dialog-editor.md)