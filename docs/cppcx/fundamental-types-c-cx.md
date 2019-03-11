---
title: Tipos fundamentales (C++/CX)
ms.date: 01/22/2017
ms.assetid: c9f82907-25f2-440b-91d6-afb8dbd46ea6
ms.openlocfilehash: 2bd5be01b868fd3086c2064edfd4ca343db425be
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57752368"
---
# <a name="fundamental-types-ccx"></a>Tipos fundamentales (C++/CX)

Además el estándares tipos integrados de C++, C / c++ / CX admite el sistema de tipos que se define mediante la arquitectura de Windows en tiempo de ejecución ofreciendo typedefs para el tiempo de ejecución de Windows fundamentales tipos que se asignan a los tipos estándar de C++... C++ / c++ / CX implementa tipos fundamentales numéricos, de carácter y un valor booleano. Estas typedefs se definen en el el espacio de nombres `default` , que nunca debe especificarse de manera explícita. Además, C / c++ / CX ofrece contenedores e implementaciones concretas para determinados tipos de Windows en tiempo de ejecución y las interfaces.

## <a name="boolean-and-character-types"></a>Tipos de caracteres y booleanos

En la tabla siguiente se muestran los tipos de caracteres y booleanos integrados, y sus equivalentes de C++ estándar.

|Espacio de nombres|C++ / c++ / nombre CX|de esquema JSON|Nombre de C++ estándar|Intervalo de valores|
|---------------|-----------------------------------------------------------------------|----------------|-------------------------|---------------------|
|Plataforma|Booleano|Un valor booleano de 8 bits.|bool|**True** (distinto de cero) y **false** (cero)|
|default|char16|Valor no numérico de 16 bits que representa un punto de código Unicode (UTF-16).|wchar_t<br /><br /> O bien<br /><br /> L'c'|(Especificado por el estándar Unicode)|

## <a name="numeric-types"></a>Tipos numéricos

En la tabla siguiente se muestran los tipos numéricos integrados. Los tipos numéricos se declaran en el espacio de nombres `default` y son typedefs para el tipo integrado de C++ correspondiente. No todos los tipos integrados de C++ (por ejemplo, long) se admiten en el tiempo de ejecución de Windows. Por coherencia y claridad, se recomienda usar C++ / c++ / nombre CX.

|C++ / c++ / nombre CX|de esquema JSON|Nombre de C++ estándar|Intervalo de valores|
|-----------------------------------------------------------------------|----------------|-------------------------|---------------------|
|int8|Valor numérico con signo de 8 bits.|signed char|-128 a 127|
|uint8|Valor numérico sin signo de 8 bits.|unsigned char|De {0} a 255|
|int16|Entero de 16 bits con signo.|short|-32.768 a 32.767|
|uint16|Entero de 16 bits sin signo.|unsigned short|De 0 a 65.535|
|int32|Entero de 32 bits con signo.|int|-2.147.483.648 a 2.147.483.647|
|uint32|Entero de 32 bits sin signo.|unsigned int|De 0 a 4.294.967.295|
|int64|Entero de 64 bits con signo.|long long - o - __int64|-9,223,372,036,854, 775,808 9.223.372.036.854.775.807|
|uint64|Entero de 64 bits sin signo.|unsigned __int64 long long - o - sin signo|De 0 a 18.446.744.073.709.551.615|
|float32|Número de punto flotante de 32 bits conforme a IEEE 754.|float|3,4E +/- 38 (7 dígitos)|
|float64|Número de punto flotante de 64 bits conforme a IEEE 754.|double|1,7E +/- 308 (15 dígitos)|

## <a name="windows-runtime-types"></a>Tipos de Windows en tiempo de ejecución

La tabla siguiente enumeran algunos tipos adicionales que se definen mediante la arquitectura en tiempo de ejecución de Windows y están integrados en C++ / c++ / CX. Object y String son tipos de referencia. Los demás son tipos de valores. Todos estos tipos se declaran en el espacio de nombres `Platform` . Para una lista completa, vea [Platform namespace](../cppcx/platform-namespace-c-cx.md).

|nombre|de esquema JSON|
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
