---
title: Servidores de documentos activos
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], servers
- servers [MFC], active document
- active document servers [MFC]
ms.assetid: 131fec1e-02a0-4305-a7ab-903b911232a7
ms.openlocfilehash: 58f2a63a8c640e6ae31640af680894763603e1d0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619138"
---
# <a name="active-document-servers"></a>Servidores de documentos activos

Servidores de documentos activos como documentos de Word, Excel o PowerPoint de otros tipos de aplicaciones denominados documentos activos. A diferencia de los objetos OLE incrustados (que simplemente se muestran en la página de otro documento), los documentos activos proporcionan la interfaz completa y la funcionalidad nativa completa de la aplicación de servidor que los crea. Los usuarios pueden crear documentos con toda la capacidad de sus aplicaciones favoritas (si están habilitadas para documentos activos), pero pueden tratar el proyecto resultante como una sola entidad.

Los documentos activos pueden tener más de una página y siempre están activos en contexto. Los documentos activos controlan parte de la interfaz de usuario, combinando sus menús con los menús **archivo** y **ayuda** del contenedor. Ocupan todo el área de edición del contenedor y controlan las vistas y el diseño de la página de la impresora (márgenes, pies de página, etc.).

MFC implementa servidores de documentos activos con interfaces de documento/vista, mapas de envío de comandos, impresión, administración de menús y administración del registro. Los requisitos de programación específicos se describen en los [documentos activos](active-documents.md).

MFC admite documentos activos con la clase [CDocObjectServer](reference/cdocobjectserver-class.md) , derivada de [CCmdTarget](reference/ccmdtarget-class.md)y [CDocObjectServerItem](reference/cdocobjectserveritem-class.md), derivadas de [COleServerItem](reference/coleserveritem-class.md). MFC admite contenedores de documentos activos con la clase [COleDocObjectItem](reference/coledocobjectitem-class.md) , derivada de [COleClientItem](reference/coleclientitem-class.md).

`CDocObjectServer`asigna las interfaces del documento activo e inicializa y activa un documento activo. MFC también proporciona macros para controlar el enrutamiento de comandos en documentos activos. Para usar documentos activos en la aplicación, incluya AfxDocOb. h en el archivo StdAfx. h.

Un servidor MFC normal enlaza su propia `COleServerItem` clase derivada. El Asistente para aplicaciones MFC genera esta clase automáticamente si activa la casilla de verificación **de servidor con** el servidor de aplicaciones o servidor **completo** para proporcionar compatibilidad con documentos compuestos del servidor de aplicaciones. Si también activa la casilla **servidor de documentos activos** , el Asistente para aplicaciones MFC genera una clase derivada de en `CDocObjectServerItem` su lugar.

La `COleDocObjectItem` clase permite que un contenedor OLE se convierta en un contenedor de documentos activo. Puede usar el Asistente para aplicaciones MFC para crear un contenedor de documentos activo activando la casilla **contenedor de documento activo** en la página compatibilidad con documentos compuestos del Asistente para aplicaciones MFC. Para obtener más información, consulte [crear una aplicación de contenedor de documentos activos](creating-an-active-document-container-application.md).

## <a name="see-also"></a>Consulte también

[Contención de documentos activos](active-document-containment.md)
