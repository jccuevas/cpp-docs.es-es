---
title: 'Controles ActiveX MFC: Métodos | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
ms.assetid: e20271de-6ffa-4ba0-848b-bafe6c9e510c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9b09de5382117b4444eb1bfd90bc0f9d447e537e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-activex-controls-methods"></a>Controles ActiveX MFC: Métodos
Un control ActiveX activa eventos para comunicarse entre sí mismo y a su contenedor de control. Un contenedor también puede comunicarse con un control mediante métodos y propiedades. Métodos también se denominan funciones.  
  
 Métodos y propiedades proporcionan una interfaz exportada para su uso por otras aplicaciones, como los clientes de automatización y contenedores de controles ActiveX. Para obtener más información sobre propiedades de controles ActiveX, vea el artículo [controles ActiveX MFC: propiedades](../mfc/mfc-activex-controls-properties.md).  
  
 Métodos son similares en uso y propósito a las funciones miembro de una clase de C++. Hay dos tipos de métodos que puede implementar el control: estándar y personalizados. Similares a los eventos estándar, los métodos estándar son aquellos métodos que [COleControl](../mfc/reference/colecontrol-class.md) proporciona una implementación. Para obtener más información sobre métodos estándar, vea el artículo [controles ActiveX de MFC: agregar métodos estándar](../mfc/mfc-activex-controls-adding-stock-methods.md). Métodos personalizados, definidos por el programador, permiten una mayor personalización del control. Para obtener más información, vea el artículo [controles ActiveX de MFC: agregar métodos personalizados](../mfc/mfc-activex-controls-adding-custom-methods.md).  
  
 La biblioteca de clases de Microsoft Foundation (MFC) implementa un mecanismo que permite al control admitir métodos estándar y personalizados. La primera parte es la clase `COleControl`. Deriva `CWnd`, `COleControl` funciones miembro admiten métodos estándar que son comunes a todos los controles de ActiveX. La segunda parte de este mecanismo es el mapa de envíos. Un mapa de envíos es similar a un mapa de mensajes; Sin embargo, en lugar de asignar una función a un identificador de mensaje de Windows, un mapa de envíos asigna funciones miembro virtuales a identificadores IDispatch.  
  
 Para que un control admitir correctamente diversos métodos, su clase debe declarar un mapa de envíos. Esto se logra mediante la siguiente línea de código que se encuentra en el encabezado de la clase de control (. H) archivo:  
  
 [!code-cpp[NVC_MFC_AxUI#13](../mfc/codesnippet/cpp/mfc-activex-controls-methods_1.h)]  
  
 El propósito principal del mapa de envíos es establecer la relación entre los nombres de método utilizados por un llamador externo (por ejemplo, el contenedor) y las funciones de miembro de la clase del control que implementan los métodos. Después de que se ha declarado el mapa de envíos, debe definirse en la implementación del control (. Archivo CPP). Las siguientes líneas de código definen el mapa de envíos:  
  
 [!code-cpp[NVC_MFC_AxUI#14](../mfc/codesnippet/cpp/mfc-activex-controls-methods_2.cpp)]  
[!code-cpp[NVC_MFC_AxUI#15](../mfc/codesnippet/cpp/mfc-activex-controls-methods_3.cpp)]  
  
 Si ha usado la [Asistente para controles ActiveX de MFC](../mfc/reference/mfc-activex-control-wizard.md) para crear el proyecto, estas líneas se agregan automáticamente. Si no se utiliza el Asistente para controles de ActiveX de MFC, debe agregar manualmente estas líneas.  
  
 Los artículos siguientes describen métodos con detalle:  
  
-   [Controles ActiveX MFC: Agregar métodos estándar](../mfc/mfc-activex-controls-adding-stock-methods.md)  
  
-   [Controles ActiveX MFC: Agregar métodos personalizados](../mfc/mfc-activex-controls-adding-custom-methods.md)  
  
-   [Controles ActiveX MFC: Devolver códigos de error desde un método](../mfc/mfc-activex-controls-returning-error-codes-from-a-method.md)  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)

