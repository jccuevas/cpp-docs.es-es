---
title: Extraer un miembro de biblioteca | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- Lib
dev_langs:
- C++
helpviewer_keywords:
- LIB [C++], extracting library members
- EXTRACT library manager option
- libraries, extracting members
- -EXTRACT library manager option
- extracting library members
- /EXTRACT library manager option
ms.assetid: a2c5c2a1-9b7e-489a-a9a4-1dec694e1fc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0dc0dc67a6d9e4a3ff61aa3b82ac10b9eabcb94b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32371247"
---
# <a name="extracting-a-library-member"></a>Extraer un miembro de biblioteca
Puede utilizar LIB para crear un archivo objeto (.obj) que contiene una copia de un miembro de una biblioteca existente. Para extraer una copia de un miembro, use la sintaxis siguiente:  
  
```  
LIB library /EXTRACT:member /OUT:objectfile  
```  
  
 Este comando crea un archivo .obj denominado *objectfile* que contiene una copia de un `member` de un *biblioteca*. El `member` nombre distingue mayúsculas de minúsculas. Puede extraer a un único miembro en un solo comando. La opción/out es necesaria; No hay ningún nombre de salida predeterminado. Si un archivo denominado *objectfile* ya existe en el directorio especificado (o el directorio actual, si no se especifica ningún directorio con *objectfile*), el texto extraído *objectfile*reemplaza el archivo existente.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de LIB](../../build/reference/lib-reference.md)