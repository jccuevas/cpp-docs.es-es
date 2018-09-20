---
title: Creación de documentos y vistas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0deb187a6540af71a1dc72b730347374bc25f963
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423080"
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

