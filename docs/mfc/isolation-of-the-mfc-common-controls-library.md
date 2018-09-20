---
title: Biblioteca de controles de aislamiento de los comunes MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, Common Controls library
ms.assetid: 7471e6f0-49b0-47f7-86e7-8d6bc3541694
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3189b2e3db594801fe417ca43867da7db2e18fd7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423785"
---
# <a name="isolation-of-the-mfc-common-controls-library"></a>Aislamiento de la biblioteca de controles comunes de MFC

La biblioteca de controles comunes ahora está aislada dentro de MFC, lo que permite a los módulos diferentes (por ejemplo, archivos DLL de usuario) para usar diferentes versiones de la biblioteca de controles comunes mediante la especificación de la versión en sus manifiestos.

Una aplicación de MFC (o código de usuario que se llamó a MFC) realiza llamadas a API a través de funciones de contenedor con nombre de biblioteca de controles comunes `Afx` *FunctionName*, donde *FunctionName* es el nombre de un común Controles de API. Las funciones contenedoras se definen en afxcomctl32.h y afxcomctl32.inl.

Puede usar el [AFX_COMCTL32_IF_EXISTS](reference/run-time-object-model-services.md#afx_comctl32_if_exists) y [AFX_COMCTL32_IF_EXISTS2](reference/run-time-object-model-services.md#afx_comctl32_if_exists2) macros (definido en afxcomctl32.h) para determinar si la biblioteca de controles comunes implementa una determinadas API en lugar de llamar [GetProcAddress](../build/getprocaddress.md).

Técnicamente, realiza llamadas a API de biblioteca de controles comunes a través de una clase contenedora, `CComCtlWrapper` (que se definen en afxcomctl32.h). `CComCtlWrapper` También es responsable de la carga y descarga de comctl32.dll. El estado del módulo MFC contiene un puntero a una instancia de `CComCtlWrapper`. Puede tener acceso a la clase de contenedor mediante el `afxComCtlWrapper` macro.

Tenga en cuenta que la llamada a API común controles directamente (sin utilizar las funciones contenedoras MFC) desde MFC aplicación o usuario DLL funcionará en la mayoría de los casos, porque la aplicación de MFC o un archivo DLL de usuario está enlazada a la biblioteca de controles comunes solicitados en su manifiesto). Sin embargo, el propio código MFC debe usar los contenedores, porque el código MFC puede llamarse desde archivos DLL de usuario con diferentes versiones de la biblioteca de controles comunes.

