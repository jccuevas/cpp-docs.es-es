---
title: Creación de documentos y vistas
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], creating
- views [MFC], and frame windows
- views [MFC], creating
- tables [MFC]
- MFC, views
- document/view architecture [MFC], creating document/view
- object creators
- MFC, documents
- tables [MFC], objects each MFC object creates
ms.assetid: bda14f41-ed50-439d-af9e-591174e7dd64
ms.openlocfilehash: 5441827188f5bff98638cc85cd29e2efd79f8ae8
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620339"
---
# <a name="documentview-creation"></a>Crear documentos y vistas

El marco de trabajo proporciona implementaciones de los comandos **nuevos** y **abiertos** (entre otros) en el menú **archivo** . La creación de un nuevo documento y su vista asociada y la ventana de marco es un esfuerzo cooperativo entre el objeto de aplicación, una plantilla de documento, el documento recién creado y la ventana de marco que se acaba de crear. En la tabla siguiente se resumen los objetos que crean qué.

### <a name="object-creators"></a>Creadores de objetos

|Creador|Crea|
|-------------|-------------|
|Objeto de aplicación|Plantilla de documento|
|Plantilla de documento|Documento|
|Plantilla de documento|Ventana marco|
|Ventana marco|Ver|

## <a name="see-also"></a>Consulte también

[Plantillas de documento y el proceso de creación de documentos y vistas](document-templates-and-the-document-view-creation-process.md)<br/>
[Creación de plantillas de documentos](document-template-creation.md)<br/>
[Relaciones entre objetos MFC](relationships-among-mfc-objects.md)<br/>
[Crear nuevos documentos, ventanas y vistas](creating-new-documents-windows-and-views.md)
