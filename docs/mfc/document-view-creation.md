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
ms.openlocfilehash: b5f9b783e8e14744a816fd63b327ed95d9da8e8a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62240797"
---
# <a name="documentview-creation"></a>Crear documentos y vistas

El marco de trabajo proporciona implementaciones de la **New** y **abierto** comandos (entre otros) en el **archivo** menú. Creación de un nuevo documento y su vista asociada y la ventana de marco es un esfuerzo cooperativo entre el objeto de aplicación, una plantilla de documento, el documento recién creado y la ventana de marco recién creado. La siguiente tabla resume los objetos que lo crean.

### <a name="object-creators"></a>Creadores de objetos

|Creator|Crea|
|-------------|-------------|
|Application (objeto)|Plantilla de documento|
|Plantilla de documento|Documento|
|Plantilla de documento|Ventana de marco|
|Ventana de marco|Ver|

## <a name="see-also"></a>Vea también

[Las plantillas de documento y el proceso de creación de documento/vista](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[Creación de plantillas de documentos](../mfc/document-template-creation.md)<br/>
[Relaciones entre objetos MFC](../mfc/relationships-among-mfc-objects.md)<br/>
[Creación de nuevos documentos, ventanas y vistas](../mfc/creating-new-documents-windows-and-views.md)
