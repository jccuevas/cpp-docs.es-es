---
title: "Identificadores de símbolo predefinidos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- symbols, predefined IDs
- predefined symbol IDs
ms.assetid: 91a5d610-1a04-47e8-b8a4-63ad650a90df
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e431ce20361a9a7d3d05676d1b9da01b98c07d5a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="predefined-symbol-ids"></a>Identificadores de símbolo predefinidos
Cuando se inicia un proyecto nuevo, dependiendo del tipo de proyecto, es posible que se hayan predefinido algunos identificadores de símbolo. Estos identificadores son compatibles con los distintos tipos de proyectos y bibliotecas (por ejemplo, MFC). Representan tareas comunes que se suelen incluir en todas las aplicaciones, o acciones de elementos de hardware, como un mouse o una impresora.  
  
 Estos identificadores de símbolo son importantes al trabajar con recursos. Se encuentran disponibles al editar tablas de aceleradores y algunos de ellos ya están asociados con teclas virtuales. También están disponibles a través del [ventana propiedades](/visualstudio/ide/reference/properties-window). Puede asignar cualquiera de los identificadores de símbolo predefinidos a los nuevos recursos, o también puede asignar a estos identificadores teclas de aceleración. En este caso, la funcionalidad asociada con el identificador de símbolo se asociará a su vez de forma automática con la combinación de teclas en cuestión.  
  
 Estas bibliotecas cuentan con símbolos predefinidos que aparecerán como parte del proyecto:  
  
-   [Símbolos predefinidos de MFC](../windows/mfc-predefined-symbols.md)  
  
-   [Símbolos predefinidos de ATL](../windows/atl-predefined-symbols.md)  
  
-   [Símbolos predefinidos de Win32](../windows/win32-predefined-symbols.md)  
  
    > [!NOTE]
    >  Los símbolos predefinidos son siempre de solo lectura.  
  

  
## <a name="requirements"></a>Requisitos  
 Win32, MFC o ATL  
  
## <a name="see-also"></a>Vea también  
 [Símbolos: Identificadores de recursos](../windows/symbols-resource-identifiers.md)