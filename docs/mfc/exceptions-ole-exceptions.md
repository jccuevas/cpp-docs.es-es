---
title: 'Excepciones: Excepciones OLE | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE, exceptions
- OLE exceptions [MFC]
- exceptions [MFC], OLE
- exception handling [MFC], OLE
- OLE exceptions [MFC], classes for handling
ms.assetid: 2f8e0161-b94f-48bb-a5a2-6f644b192527
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 991848e9b5b78ad960fb8ed0bdf09dd56db47e2c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="exceptions-ole-exceptions"></a>Excepciones: Excepciones OLE
Las técnicas y herramientas para controlar las excepciones en OLE son los mismos que para el control de otras excepciones. Para obtener más información sobre control de excepciones, vea el artículo [control de excepciones de C++](../cpp/cpp-exception-handling.md).  
  
 Todos los objetos de excepción se derivan de la clase base abstracta `CException`. MFC proporciona dos clases para controlar las excepciones de OLE:  
  
-   [COleException](../mfc/reference/coleexception-class.md) para controlar las excepciones generales de OLE.  
  
-   [COleDispatchException](../mfc/reference/coledispatchexception-class.md) para generar y controlar OLE enviar excepciones (automatización).  
  
 La diferencia entre estas dos clases es la cantidad de información que proporcionan y que se utilizan. `COleException` tiene un miembro de datos públicos que contiene el código de estado OLE para la excepción. `COleDispatchException` proporciona más información, incluidas las siguientes:  
  
-   Un código de error específica de la aplicación  
  
-   Una descripción del error, como "Disco lleno"  
  
-   Un contexto de ayuda que la aplicación puede usar para proporcionar información adicional para el usuario  
  
-   El nombre del archivo de Ayuda de la aplicación  
  
-   El nombre de la aplicación que generó la excepción  
  
 `COleDispatchException` proporciona más información para que se puede utilizar con productos como Microsoft Visual Basic. La descripción del error puede usarse en un cuadro de mensaje u otra notificación; la información de ayuda puede utilizarse para ayudar al usuario a responder a las condiciones que causaron la excepción.  
  
 Dos funciones globales corresponden a las dos clases de excepción OLE: [AfxThrowOleException](../mfc/reference/exception-processing.md#afxthrowoleexception) y [AfxThrowOleDispatchException](../mfc/reference/exception-processing.md#afxthrowoledispatchexception). Úselas para iniciar excepciones generales OLE y excepciones de envío OLE, respectivamente.  
  
## <a name="see-also"></a>Vea también  
 [Control de excepciones](../mfc/exception-handling-in-mfc.md)

