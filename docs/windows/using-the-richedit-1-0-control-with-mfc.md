---
title: Utilizar el Control RichEdit 1.0 con MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- RichEdit 1.0 control
- rich edit controls [C++], RichEdit 1.0
ms.assetid: 5a9060dd-44d8-4ef3-956e-16152f7e23d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 27e3ad32500d1b0ff0efa2dab40888f163744bb1
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44318712"
---
# <a name="using-the-richedit-10-control-with-mfc"></a>Utilizar el control RichEdit 1.0 con MFC

Para utilizar un control RichEdit, primero debe llamar a [AfxInitRichEdit2](../mfc/reference/application-information-and-management.md#afxinitrichedit2) para cargar el Control RichEdit 2.0 (RICHED20. Archivo DLL), o llamar a [AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit) para cargar el Control RichEdit 1.0 anterior (RICHED32. (DLL).

Puede usar actual [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) clase con el control RichEdit 1.0 anterior, pero `CRichEditCtrl` sólo está diseñada para admitir el control RichEdit 2.0. Dado que RichEdit 1.0 y RichEdit 2.0 son muy similares, funcionará la mayoría de los métodos; Sin embargo, observe que hay algunas diferencias entre los controles 1.0 y 2.0, por lo que algunos métodos podrían no funcionen correctamente o no funcionará en absoluto.

## <a name="requirements"></a>Requisitos

MFC

## <a name="see-also"></a>Vea también

[Solucionar problemas del Editor de cuadros de diálogo](../windows/troubleshooting-the-dialog-editor.md)  
[Editor de cuadros de diálogo](../windows/dialog-editor.md)