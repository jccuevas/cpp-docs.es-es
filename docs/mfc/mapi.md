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
ms.openlocfilehash: a5f60e1ba8c2b68ddca312859694f532e38da965
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279112"
---
# <a name="mapi"></a>MAPI

En este artículo se describe la interfaz de programación de aplicaciones de mensajería de Microsoft (MAPI) para desarrolladores de aplicaciones de mensaje de cliente. MFC proporciona compatibilidad con un subconjunto de MAPI en clase `CDocument` pero no encapsula toda la API. Para obtener más información, consulte [compatibilidad MAPI en MFC](../mfc/mapi-support-in-mfc.md).

MAPI es un conjunto de funciones que usan aplicaciones basadas en correo electrónico y habilitados para correo electrónico para crear, manipular, transferir y almacenar mensajes de correo. Ofrece las herramientas para definir el propósito y el contenido de los mensajes de correo electrónico de los desarrolladores de aplicaciones y proporciona flexibilidad para administrar los mensajes almacenados. MAPI también proporciona una interfaz común que los desarrolladores de aplicaciones pueden usar para crear habilitados para correo electrónico y aplicaciones basadas en el correo electrónico independientes del sistema de mensajería subyacente.

Los clientes de mensajería proporcionan una interfaz de usuario para la interacción con el sistema de mensajería de Windows (WMS) de Microsoft. Esta interacción suele incluir solicitar los servicios de proveedores compatibles con MAPI, como almacenes de mensajes y libretas de direcciones.

Para obtener más información acerca de MAPI, vea los artículos en la Guía de Win32 de mensajería (MAPI) del SDK de Windows.

## <a name="in-this-section"></a>En esta sección

[Compatibilidad MAPI en MFC](../mfc/mapi-support-in-mfc.md)

## <a name="see-also"></a>Vea también

[CDocument::OnFileSendMail](../mfc/reference/cdocument-class.md#onfilesendmail)<br/>
[CDocument::OnUpdateFileSendMail](../mfc/reference/cdocument-class.md#onupdatefilesendmail)<br/>
[COleDocument::OnFileSendMail](../mfc/reference/coledocument-class.md#onfilesendmail)
