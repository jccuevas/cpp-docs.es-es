---
title: implementation_only | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: implementation_only
dev_langs: C++
helpviewer_keywords: implementation_only attribute
ms.assetid: d8cabc86-4425-45a0-9587-d57536980088
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7a033cd4b1618c2da106bb641f55c9ae967cd53a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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