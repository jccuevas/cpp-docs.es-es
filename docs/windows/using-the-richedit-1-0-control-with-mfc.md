---
title: Utilizar el Control RichEdit 1.0 con MFC | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- RichEdit 1.0 control
- rich edit controls, RichEdit 1.0
ms.assetid: 5a9060dd-44d8-4ef3-956e-16152f7e23d2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f8085eb8b28ece4f0ca24d00c33b8809aa412da5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="using-the-richedit-10-control-with-mfc"></a>Utilizar el control RichEdit 1.0 con MFC
Para utilizar un control RichEdit, primero debe llamar a [AfxInitRichEdit2](../mfc/reference/application-information-and-management.md#afxinitrichedit2) para cargar el Control RichEdit 2.0 (RICHED20.) DLL), o llamar a [AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit) para cargar el Control RichEdit 1.0 anterior (RICHED32. (DLL).  
  
 Puede usar actual [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) clase con el control RichEdit 1.0 anterior, pero **CRichEditCtrl** sólo está diseñado para admitir el control RichEdit 2.0. Dado que RichEdit 1.0 y RichEdit 2.0 son muy similares, la mayoría de los métodos funcionarán; Tenga en cuenta sin embargo, hay algunas diferencias entre los controles 1.0 y 2.0, por lo que algunos métodos podrían no funcionen correctamente o no funcionará en absoluto.  
  
## <a name="requirements"></a>Requisitos  
 MFC  
  
## <a name="see-also"></a>Vea también  
 [Solucionar problemas del Editor de cuadro de diálogo](../windows/troubleshooting-the-dialog-editor.md)   
 [Editor de cuadros de diálogo](../windows/dialog-editor.md)

