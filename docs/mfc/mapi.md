---
title: MAPI | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- messaging [MFC], client applications
- enabling applications for MAPI [MFC]
- MAPI support in MFC
- e-mail [MFC], enabling
- mail [MFC], enabling your application
- MAPI, MFC
- enabling applications for mail [MFC]
ms.assetid: 193449f7-b131-4ab0-9301-8d4f6cd1e7c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 19615aabce489049d38539b48300311504fbbbfe
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="mapi"></a>MAPI
Este artículo se describe la interfaz de programación de aplicaciones de mensajería de Microsoft (MAPI) para desarrolladores de aplicaciones de mensaje de cliente. MFC proporciona compatibilidad con un subconjunto de MAPI en clase **CDocument** pero no encapsula toda la API. Para obtener más información, consulte [compatibilidad MAPI en MFC](../mfc/mapi-support-in-mfc.md).  
  
 MAPI es un conjunto de funciones que las aplicaciones habilitados para correo y tenga en cuenta de correo electrónico que se usan para crear, manipular, transferir y almacenar mensajes de correo. Proporciona las herramientas para definir el propósito y el contenido de los mensajes de correo electrónico de los desarrolladores de aplicaciones y le da flexibilidad para administrar los mensajes de correo electrónico almacenado. MAPI también proporciona una interfaz común que los desarrolladores de aplicaciones pueden usar para crear habilitados para correo y aplicaciones compatibles con el correo electrónico independientes del sistema de mensajería subyacente.  
  
 Los clientes de mensajería proporcionan una interfaz de usuario para la interacción con el sistema de mensajería de Windows (WMS) de Microsoft. Normalmente, esta interacción permite solicitar los servicios de proveedores compatibles con MAPI, como almacenes de mensajes y libretas de direcciones.  
  
 Para obtener más información acerca de MAPI, vea los artículos en la Guía de Win32 de mensajería (MAPI) del SDK de Windows.  
  
## <a name="in-this-section"></a>En esta sección  
 [Compatibilidad MAPI en MFC](../mfc/mapi-support-in-mfc.md)  
  
## <a name="see-also"></a>Vea también  
 [CDocument:: OnFileSendMail](../mfc/reference/cdocument-class.md#onfilesendmail)   
 [CDocument:: OnUpdateFileSendMail](../mfc/reference/cdocument-class.md#onupdatefilesendmail)   
 [COleDocument::OnFileSendMail](../mfc/reference/coledocument-class.md#onfilesendmail)

