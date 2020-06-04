---
title: Servidores de documentos activos
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], servers
- servers [MFC], active document
- active document servers [MFC]
ms.assetid: 131fec1e-02a0-4305-a7ab-903b911232a7
ms.openlocfilehash: 7050b810bb5e1f0c240222cd9b8c4922ced4238a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394980"
---
# <a name="active-document-servers"></a>Servidores de documentos activos

Servidores de documentos activos, como Word, Excel o PowerPoint, documentos de host de otros tipos de aplicación llaman documentos activos. A diferencia de OLE objetos incrustados (que sólo se muestran en la página de otro documento), documentos activos proporcionan la interfaz completa y toda la funcionalidad nativa de la aplicación de servidor que las crea. Los usuarios pueden crear documentos usando toda la eficacia de sus aplicaciones favoritas (si están habilitada de documento activo), todavía puede tratar el proyecto resultante como una sola entidad.

Documentos activos pueden tener más de una página y siempre activo en contexto. Documentos activos controlan parte de la interfaz de usuario, combinando sus menús con el **archivo** y **ayuda** menús del contenedor. Se ocupa toda el área de edición del contenedor y controlan las vistas y el diseño de la página de la impresora (márgenes, pies de página y así sucesivamente).

MFC implementa servidores de documentos activos con interfaces de documento/vista, mapas de envío de comandos, impresión, administración de menús y administración del registro. Requisitos de programación específicos se describen en [documentos activos](../mfc/active-documents.md).

MFC admite documentos activos con el [CDocObjectServer](../mfc/reference/cdocobjectserver-class.md) clase, derivada de [CCmdTarget](../mfc/reference/ccmdtarget-class.md), y [CDocObjectServerItem](../mfc/reference/cdocobjectserveritem-class.md), derivada de [ COleServerItem](../mfc/reference/coleserveritem-class.md). MFC admite contenedores de documentos activos con el [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md) clase, derivada de [COleClientItem](../mfc/reference/coleclientitem-class.md).

`CDocObjectServer` asigna las interfaces de documento activo, inicializa y activa un documento activo. MFC también proporciona macros para controlar el enrutamiento de comandos en documentos activos. Para usar documentos activos en la aplicación, incluya AfxDocOb.h en el archivo StdAfx.h.

Un servidor normal de MFC enlaza su propio `COleServerItem`-clase derivada. El Asistente para aplicaciones MFC genera esta clase para usted si selecciona el **miniservidor** o **servidor completo** casilla de verificación para proporcionar compatibilidad con documentos compuestos a su servidor de aplicaciones. Si también selecciona el **servidor de documentos activos** casilla de verificación, el Asistente para aplicaciones MFC genera una clase derivada de `CDocObjectServerItem` en su lugar.

La `COleDocObjectItem` clase permite que un contenedor OLE para convertirse en un contenedor de documentos activos. Puede usar el Asistente para aplicaciones MFC para crear un contenedor de documentos activos seleccionando el **contenedor de documentos activos** casilla de verificación en la página de compatibilidad con documentos compuestos de MFC Application Wizard. Para obtener más información, consulte [crear una aplicación de contenedor de documentos activos](../mfc/creating-an-active-document-container-application.md).

## <a name="see-also"></a>Vea también

[Contención de documentos activos](../mfc/active-document-containment.md)
