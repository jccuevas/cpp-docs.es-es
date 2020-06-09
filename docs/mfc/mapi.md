---
title: MAPI
ms.date: 11/04/2016
helpviewer_keywords:
- messaging [MFC], client applications
- enabling applications for MAPI [MFC]
- MAPI support in MFC
- e-mail [MFC], enabling
- mail [MFC], enabling your application
- MAPI, MFC
- enabling applications for mail [MFC]
ms.assetid: 193449f7-b131-4ab0-9301-8d4f6cd1e7c4
ms.openlocfilehash: 0008a2bc433401f3e048b6f5a92cded88114d08e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625552"
---
# <a name="mapi"></a>MAPI

En este artículo se describe la interfaz de programación de aplicaciones de mensajería (MAPI) de Microsoft para programadores de aplicaciones de mensajes de cliente. MFC proporciona compatibilidad con un subconjunto de MAPI en `CDocument` la clase, pero no encapsula toda la API. Para obtener más información, consulte [compatibilidad con MAPI en MFC](mapi-support-in-mfc.md).

MAPI es un conjunto de funciones que las aplicaciones habilitadas para correo electrónico y para correo utilizan para crear, manipular, transferir y almacenar mensajes de correo electrónico. Ofrece a los desarrolladores de aplicaciones las herramientas para definir el propósito y el contenido de los mensajes de correo y les da flexibilidad en la administración de los mensajes de correo almacenados. MAPI también proporciona una interfaz común que los desarrolladores de aplicaciones pueden utilizar para crear aplicaciones habilitadas para correo y para correo independientes del sistema de mensajería subyacente.

Los clientes de mensajería proporcionan una interfaz de usuario para la interacción con el sistema de mensajería de Microsoft Windows (WMS). Esta interacción normalmente incluye servicios de solicitud de proveedores compatibles con MAPI, como almacenes de mensajes y libretas de direcciones.

Para obtener más información acerca de MAPI, consulte los artículos de la guía de mensajería Win32 (MAPI) de la Windows SDK.

## <a name="in-this-section"></a>En esta sección

[Compatibilidad con MAPI en MFC](mapi-support-in-mfc.md)

## <a name="see-also"></a>Consulte también

[CDocument:: OnFileSendMail](reference/cdocument-class.md#onfilesendmail)<br/>
[CDocument:: OnUpdateFileSendMail](reference/cdocument-class.md#onupdatefilesendmail)<br/>
[COleDocument:: OnFileSendMail](reference/coledocument-class.md#onfilesendmail)
