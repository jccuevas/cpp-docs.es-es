---
title: Tipos fundamentales (C++ / CX) | Documentos de Microsoft
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9f82907-25f2-440b-91d6-afb8dbd46ea6
caps.latest.revision: "14"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a41a5a97e94bdf9476d8345a7f9e103b81466f6e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="fundamental-types-ccx"></a>Tipos fundamentales (C++/CX)
Además el estándar C++ tipos integrados, C++ / CX admite el sistema de tipos que se define mediante la arquitectura de Windows Runtime ofreciendo typedefs para los tipos de Windows Runtime fundamentales que se asignan a los tipos de C++ estándar... C++ / CX implementa tipos fundamentales numéricos, caracteres y un valor booleano. Estas typedefs se definen en el el espacio de nombres `default` , que nunca debe especificarse de manera explícita. Además, C++ / CX ofrece contenedores e implementaciones concretas para determinados tipos de Windows Runtime y las interfaces.  
  
## <a name="boolean-and-character-types"></a>Tipos de caracteres y booleanos  
 En la tabla siguiente se muestran los tipos de caracteres y booleanos integrados, y sus equivalentes de C++ estándar.  
  
|Espacio de nombres|C++ / nombre CX|Definición|Nombre de C++ estándar|Intervalo de valores|  
|---------------|-----------------------------------------------------------------------|----------------|-------------------------|---------------------|  
|Plataforma|Booleano|Un valor booleano de 8 bits.|bool|`true` (distinto de cero) y `false` (cero)|  
|default|char16|Valor no numérico de 16 bits que representa un punto de código Unicode (UTF-16).|wchar_t<br /><br /> O bien<br /><br /> L'c'|(Especificado por el estándar Unicode)|  
  
## <a name="numeric-types"></a>Tipos numéricos  
 En la tabla siguiente se muestran los tipos numéricos integrados. Los tipos numéricos se declaran en el espacio de nombres `default` y son typedefs para el tipo integrado de C++ correspondiente. No todos los tipos integrados de C++ (por ejemplo, long) se admiten en el tiempo de ejecución de Windows. Para lograr coherencia y claridad, se recomienda utilizar C++ / nombre CX.  
  
|C++ / nombre CX|Definición|Nombre de C++ estándar|Intervalo de valores|  
|-----------------------------------------------------------------------|----------------|-------------------------|---------------------|  
|int8|Valor numérico con signo de 8 bits.|signed char|-128 a 127|  
|uint8|Valor numérico sin signo de 8 bits.|unsigned char|De {0} a 255|  
|int16|Entero de 16 bits con signo.|short|-32.768 a 32.767|  
|uint16|Entero de 16 bits sin signo.|unsigned short|De 0 a 65.535|  
|int32|Entero de 32 bits con signo.|int|-2.147.483.648 a 2.147.483.647|  
|uint32|Entero de 32 bits sin signo.|unsigned int|De 0 a 4.294.967.295|  
|int64|Entero de 64 bits con signo.|long long - o - __int64|-9,223,372,036,854, 775,808 a 9.223.372.036.854.775.807|  
|uint64|Entero de 64 bits sin signo.|__int64 sin signo long long - o bien - sin signo|De 0 a 18.446.744.073.709.551.615|  
|float32|Número de punto flotante de 32 bits conforme a IEEE 754.|float|3,4E +/- 38 (7 dígitos)|  
|float64|Número de punto flotante de 64 bits conforme a IEEE 754.|double|1,7E +/- 308 (15 dígitos)|  
  
## <a name="windows-runtime-types"></a>Tipos de tiempo de ejecución de Windows  
 En la tabla siguiente se muestra algunos otros tipos que se definen mediante la arquitectura en tiempo de ejecución de Windows y están integrados en C++ / CX. Object y String son tipos de referencia. Los demás son tipos de valores. Todos estos tipos se declaran en el espacio de nombres `Platform` . Para una lista completa, vea [Platform namespace](../cppcx/platform-namespace-c-cx.md).  
  
|nombre|Definición|  
|----------|----------------|  
|Object|Representa cualquier tipo en tiempo de ejecución de Windows.|  
|String|Serie de caracteres que representan texto.|  
|Rect|Conjunto de cuatro números de punto flotante que representan la posición y el tamaño de un rectángulo.|  
|SizeT|Par ordenado de números de punto flotante que especifican un alto y un ancho.|  
|Punto|Par ordenado de coordenadas x de punto flotante y coordenadas y que definen un punto en un plano bidimensional.|  
|GUID|Valor no numérico de 128 bits que se usa como identificador único.|  
|UIntPtr|(Solo para uso interno.) Valor de 64 bits sin signo que se usa como puntero.|  
|IntPtr|(Solo para uso interno.)  Valor de 64 bits con signo que se usa como puntero.|  
  
## <a name="see-also"></a>Vea también  
 [Sistema de tipos](../cppcx/type-system-c-cx.md)