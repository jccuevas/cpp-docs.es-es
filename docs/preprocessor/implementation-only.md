---
title: implementation_only | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- implementation_only
dev_langs:
- C++
helpviewer_keywords:
- implementation_only attribute
ms.assetid: d8cabc86-4425-45a0-9587-d57536980088
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a3a2cbf0b39dc1c5f5462ae105e2206d70a38f4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33912828"
---
# <a name="implementationonly"></a>implementation_only
**Específicos de C++**  
  
 Suprime la generación de archivos de encabezado .tlh (el archivo de encabezado principal).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
implementation_only  
```  
  
## <a name="remarks"></a>Comentarios  
 Este archivo contiene todas las declaraciones utilizadas para exponer el contenido de la biblioteca de tipos. El archivo de encabezado .tli, con las implementaciones de las funciones miembro del contenedor, se genera y se incluye en la compilación.  
  
 Cuando se especifica este atributo, el contenido del encabezado .tli está en el mismo espacio de nombres que el utilizado normalmente en el encabezado .tlh. Además, las funciones miembro no se declaran como alineadas.  
  
 El `implementation_only` atributo está pensado para su uso junto con el [no_implementation](../preprocessor/no-implementation.md) atributo como una manera de mantener las implementaciones fuera del archivo de encabezado precompilado (PCH). Una instrucción `#import` con el atributo `no_implementation` se coloca en la región de origen usada para crear el PCH. Varios archivos de código fuente utilizan el PCH resultante. Una instrucción `#import` con el atributo `implementation_only` se utiliza entonces fuera de la región de PCH. Debe usar esta instrucción una sola vez en uno de los archivos de código fuente. Esto generará todas las funciones miembro del contenedor necesarias sin necesidad de recompilación adicional para cada archivo de código fuente.  
  
> [!NOTE]
>  El atributo `implementation_only` de una instrucción `#import` debe usarse junto con otra instrucción `#import`, de la misma biblioteca de tipos, con el atributo `no_implementation`. De lo contrario, se generarán errores de compilador. Esto es porque las definiciones de clase de contenedor generadas por la instrucción `#import` con el atributo `no_implementation` son necesarias para compilar las implementaciones generadas por el atributo `implementation_only`.  
  
 **FIN de específicos de C++**  
  
## <a name="see-also"></a>Vea también  
 [atributos #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import (directiva)](../preprocessor/hash-import-directive-cpp.md)