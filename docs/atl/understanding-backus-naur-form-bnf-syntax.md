---
title: El registrador de ATL y la sintaxis de forma de Backus-Naur (BNF)
ms.date: 05/14/2019
helpviewer_keywords:
- BNF notation
- Backus-Naur form (BNF) syntax
ms.assetid: 994bbef0-9077-4aa8-bdfe-b7e830af9acc
ms.openlocfilehash: 0f07a39863b586d524d060dc3df7117e2c930b3e
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168714"
---
# <a name="understanding-backus-naur-form-bnf-syntax"></a>Conceptos sobre la sintaxis de forma de Backus-Naur (BNF)

En este tema, los scripts que usa el registrador de ATL se describen mediante la sintaxis de BNF, en la que se usa la notación que se muestra en la tabla siguiente.

|Convención/símbolo|Significado|
|------------------------|-------------|
|::=|Tipo de datos de XPath|
|&#124;|O BIEN|
|X+|Una o varias X.|
|\[X]|X es opcional. Los delimitadores opcionales se indican mediante \[].|
|Cualquier texto en **negrita**|Un literal de cadena.|
|Cualquier texto *en cursiva*|Cómo construir el literal de cadena.|

Como se indica en la tabla anterior, en los scripts de registrador se usan literales de cadena. Estos valores son texto real que debe aparecer en el script. En la tabla siguiente se describen los literales de cadena que se usan en un script de registrador de ATL.

|Literal de cadena|Acción|
|--------------------|------------|
|**ForceRemove**|Quita completamente la clave siguiente (si existe) y, después, la vuelve a crear.|
|**NoRemove**|No quita la clave siguiente durante Anular registro.|
|**Val**|Especifica que `<Key Name>` es realmente un valor con nombre.|
|**Eliminar**|Quita la clave siguiente durante Registrar.|
|**seg**|Especifica que el valor siguiente es una cadena (REG_SZ).|
|**d**|Especifica que el valor siguiente es una instancia de DWORD (REG_DWORD).|
|**f**|Especifica que el valor siguiente es una instancia de MultiString (REG_MULTI_SZ).|
|**b**|Especifica que el valor siguiente es un valor binario (REG_BINARY).|

## <a name="bnf-syntax-examples"></a>Ejemplos de sintaxis BNF

Estos son algunos ejemplos de sintaxis que le ayudarán a comprender cómo funcionan los literales de cadena y la notación en un script de registrador de ATL.

### <a name="syntax-example-1"></a>Ejemplo de sintaxis 1

> \<expresión del registro>:: \<= agregar clave>

Especifica que `registry expression` es equivalente a `Add Key`.

### <a name="syntax-example-2"></a>Ejemplo de sintaxis 2

> \<expresión del registro>:: \<= agregar clave> | \<Eliminar> de clave

Especifica que `registry expression` es equivalente a `Add Key` o a `Delete Key`.

### <a name="syntax-example-3"></a>Ejemplo de sintaxis 3

> \<Nombre de clave>:: =\<' alfanumérica>+ '

Especifica que `Key Name` es equivalente a uno o varios `AlphaNumeric` valores.

### <a name="syntax-example-4"></a>Ejemplo de sintaxis 4

> \<Agregar clave>:: = [**ForceRemove** | **noremove** | **Val**]\<nombre de clave>

Especifica que `Add Key` es equivalente a `Key Name` y que los literales de cadena, `ForceRemove`, `NoRemove` y `val`, son opcionales.

### <a name="syntax-example-5"></a>Ejemplo de sintaxis 5

> \<> alfanumérica:: = *cualquier carácter que no sea NULL, es decir, ASCII 0*

Especifica que `AlphaNumeric` es equivalente a cualquier carácter distinto de NULL.

### <a name="syntax-example-6"></a>Ejemplo de sintaxis 6

```rgs
val 'testmulti' = m 'String 1\0String 2\0'
```

Especifica que el nombre de clave `testmulti` es un valor MultiString formado por `String 1` y `String 2`.

### <a name="syntax-example-7"></a>Ejemplo de sintaxis 7

```rgs
val 'testhex' = d '&H55'
```

Especifica que el nombre de clave `testhex` es un valor DWORD que se establece en 55 hexadecimal (85 decimal). Tenga en cuenta que este formato se ajusta a la notación **&H** como aparece en la especificación de Visual Basic.

## <a name="see-also"></a>Consulte también

[Crear scripts de registrador](../atl/creating-registrar-scripts.md)
