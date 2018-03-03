---
title: SECCIONES) (C/C ++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SECTIONS
dev_langs:
- C++
helpviewer_keywords:
- SECTIONS .def file statement
ms.assetid: 7b974366-9ef5-4e57-bbcc-73a1df6f8857
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0ab2f021a53e8ae685891863500feb3873e13e2e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="sections-cc"></a>SECTIONS (C/C++)
Presenta una sección de uno o varios `definitions` que son especificadores de acceso en secciones en el archivo de salida del proyecto.  
  
```  
SECTIONS  
definitions  
```  
  
## <a name="remarks"></a>Comentarios  
 Cada definición debe estar en una línea independiente. El `SECTIONS` palabra clave puede estar en la misma línea que la primera definición o en una línea anterior. El archivo .def puede contener uno o más `SECTIONS` las instrucciones.  
  
 Esto `SECTIONS` instrucción establece los atributos de una o varias secciones en el archivo de imagen y puede utilizarse para reemplazar los atributos predeterminados para cada tipo de sección.  
  
 El formato de `definitions` es:  
  
 `.section_name specifier`  
  
 donde `.section_name` es el nombre de una sección en la imagen del programa y `specifier` es uno o varios de los siguientes modificadores de acceso:  
  
|Modificador|Descripción|  
|--------------|-----------------|  
|`EXECUTE`|La sección es ejecutable|  
|`READ`|Permite operaciones de lectura en datos|  
|`SHARED`|Comparte la sección entre todos los procesos que cargan la imagen|  
|`WRITE`|Permite operaciones de escritura en los datos|  
  
 Separe los nombres de especificadores con un espacio. Por ejemplo:  
  
```  
SECTIONS  
.rdata READ WRITE  
```  
  
 `SECTIONS`marca el principio de una lista de sección `definitions`. Cada `definition` debe estar en una línea independiente. El `SECTIONS` palabra clave puede estar en la misma línea que la primera `definition` o en una línea anterior. El archivo .def puede contener uno o más `SECTIONS` las instrucciones. El `SEGMENTS` (palabra clave) se admite como sinónimo de `SECTIONS`.  
  
 Se admiten las versiones anteriores de Visual C++:  
  
```  
section [CLASS 'classname'] specifier  
```  
  
 El `CLASS` palabra clave se admite por compatibilidad, pero se omite.  
  
 Es una manera equivalente para especificar atributos de la sección con la [/SECTION](../../build/reference/section-specify-section-attributes.md) opción.  
  
## <a name="see-also"></a>Vea también  
 [Reglas para instrucciones de definición de módulos](../../build/reference/rules-for-module-definition-statements.md)