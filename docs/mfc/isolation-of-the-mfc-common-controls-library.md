---
title: Biblioteca de controles de aislamiento de MFC Common | Documentos de Microsoft
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
ms.openlocfilehash: 193a0ea527cda3819a585f5b7149c823a7eb8ef7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346820"
---
# <a name="isolation-of-the-mfc-common-controls-library"></a>Aislamiento de la biblioteca de controles comunes de MFC
La biblioteca de controles comunes ahora está aislada dentro de MFC, lo que permite módulos diferentes (por ejemplo, archivos DLL de usuario) que utilizan versiones diferentes de la biblioteca de controles comunes mediante la especificación de la versión en sus manifiestos.  
  
 Una aplicación MFC (y el código de usuario llama a MFC) realiza llamadas a las API a través de funciones de contenedor con el nombre de biblioteca de controles comunes `Afx` *FunctionName*, donde *FunctionName* es el nombre de un comunes Controles de API. Las funciones de contenedor se definen en afxcomctl32.h y afxcomctl32.inl.  
  
 Puede usar el [AFX_COMCTL32_IF_EXISTS](reference/run-time-object-model-services.md#afx_comctl32_if_exists) y [AFX_COMCTL32_IF_EXISTS2](reference/run-time-object-model-services.md#afx_comctl32_if_exists2) macros (definido en afxcomctl32.h) para determinar si la biblioteca de controles comunes implementa una determinada API en lugar de llamar [GetProcAddress](../build/getprocaddress.md).  
  
 Técnicamente, realiza llamadas a las API de la biblioteca de controles comunes a través de una clase contenedora, `CComCtlWrapper` (definido en afxcomctl32.h). `CComCtlWrapper` También es responsable de la carga y descarga de comctl32.dll. El estado del módulo MFC contiene un puntero a una instancia de `CComCtlWrapper`. Puede tener acceso a la clase de contenedor utilizando las `afxComCtlWrapper` macro.  
  
 Tenga en cuenta que la llamada a API común de controles directamente (sin utilizar las funciones de contenedor MFC) desde un MFC aplicación o un archivo DLL de usuario funcionará en la mayoría de los casos, porque la aplicación de MFC o un archivo DLL de usuario está enlazada a la biblioteca de controles comunes que solicitan en su manifiesto). Sin embargo, el propio código MFC se tiene que utilizar los contenedores, dado que se llame a código MFC de archivos DLL de usuario con diferentes versiones de la biblioteca de controles comunes.

