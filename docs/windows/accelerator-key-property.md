---
title: Propiedad de clave de Acelerador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: Key property
ms.assetid: d1570cd9-b414-4cd6-96bd-47c38281eaca
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 365960717f5fe4cedf79615fd3087bc89d6b531c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="accelerator-key-property"></a>Key (Propiedad de acelerador)
Las entradas siguientes son válidas para la propiedad de clave en la tabla de aceleradores:  
  
-   Un entero entre 0 y 255 en formato decimal. El valor determina si el valor se trata como ASCII o ANSI como sigue:  
  
    -   Números de un solo dígito se interpretan siempre como la clave correspondiente, en lugar de como valores ASCII o ANSI.  
  
    -   Valores de 1 a 26, si van precedidos de ceros, se interpretan como ^ A ^ Z, que representa el valor ASCII de las letras del alfabeto cuando se presionan mantenidos presionada la tecla CTRL.  
  
    -   Valores de 27-32 siempre se interpretan como valores de tres dígitos decimales comprendidos entre 032 027.  
  
    -   Los valores de 033 a 255, si va precedido por 0 o no se interpretan como valores ANSI.  
  
-   Un carácter aislado del teclado. Mayúsculas A - Z o los números 0 - 9 pueden ser ASCII o valores de clave virtuales; cualquier otro carácter solo es ASCII.  
  
-   Un carácter único teclado dentro del intervalo A - Z (sólo mayúsculas) y precedido por un símbolo de intercalación (^) (por ejemplo, ^ C). Este modo especifica el valor ASCII de la clave cuando se presiona con manteniendo presionada la tecla CTRL.  
  
    > [!NOTE]
    >  Cuando escribe un valor ASCII, las opciones de la propiedad modificador son limitadas. La única clave de control disponible para su uso es la tecla ALT.  
  
-   Cualquier identificador de clave virtual válido. El cuadro de lista desplegable clave en la tabla de aceleradores contiene una lista de identificadores de tecla virtuales estándar.  
  
    > [!TIP]
    >  Es otra manera de definir una tecla de aceleración (ratón) en una o varias entradas en la tabla de aceleradores, elegir **tecla siguiente** en el menú contextual y, a continuación, presione cualquiera de las claves o combinaciones de teclas del teclado. El **tecla siguiente** comando también está disponible en la **editar** menú.  
  
## <a name="requirements"></a>Requisitos  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Establecer las propiedades de Acelerador](../windows/setting-accelerator-properties.md)   
 [Edición en una tabla de aceleradores](../windows/editing-in-an-accelerator-table.md)   
 [Editor de aceleradores](../windows/accelerator-editor.md)