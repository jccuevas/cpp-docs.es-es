---
title: Portapapeles | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- cutting and copying data
- copying data
- Clipboard
- Clipboard, programming
- transferring data
ms.assetid: a71b2824-1f14-4914-8816-54578d73ad4e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f2ad21bcbff31335f6ec79a4527ef7d99e07e547
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341109"
---
# <a name="clipboard"></a>Portapapeles
Esta serie de artículos explica cómo implementar la compatibilidad con el Portapapeles de Windows en aplicaciones MFC. El Portapapeles de Windows se utiliza de dos maneras:  
  
-   Implementación de comandos del menú Edición estándares, como cortar, copiar y pegar.  
  
-   Implementación de datos uniformes transferir con arrastrar y colocar (OLE).  
  
 El Portapapeles es el método de Windows estándar de transferencia de datos entre un origen y un destino. También puede ser muy útil en operaciones OLE. Con la llegada de OLE, hay dos mecanismos del Portapapeles en Windows. La API del Portapapeles de Windows estándar sigue estando disponible, pero se ha complementado con el mecanismo de transferencia de datos OLE. Transferencia de datos uniforme (UDT) de OLE admite Cortar, copiar y pegar con el Portapapeles y arrastrar y colocar.  
  
 El Portapapeles es un servicio de sistema compartido por toda la sesión de Windows, por lo que no tiene un identificador o una clase de su propio. Administrar el Portapapeles mediante las funciones miembro de clase [CWnd](../mfc/reference/cwnd-class.md).  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Cuándo usar cada mecanismo del Portapapeles](../mfc/clipboard-when-to-use-each-clipboard-mechanism.md)  
  
-   [Mediante la API de Portapapeles tradicional de Windows](../mfc/clipboard-using-the-windows-clipboard.md)  
  
-   [Usar el mecanismo del Portapapeles de OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)  
  
-   [Copiar y pegar datos](../mfc/clipboard-copying-and-pasting-data.md)  
  
-   [Agregar otros formatos](../mfc/clipboard-adding-other-formats.md)  
  
-   [El Portapapeles de Windows](https://msdn.microsoft.com/library/ms648709)  
  
-   [Implementación de arrastrar y colocar (OLE)](../mfc/drag-and-drop-ole.md)  
  
## <a name="see-also"></a>Vea también  
 [Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)
