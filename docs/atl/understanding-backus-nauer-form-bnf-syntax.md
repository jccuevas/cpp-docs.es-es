---
title: Registrador de ATL y la forma de Backus Nauer forman la sintaxis (BNF) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BNF notation
- Backus Nauer Form (BNF) syntax
ms.assetid: 994bbef0-9077-4aa8-bdfe-b7e830af9acc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e615068580bcc9078959cc6cdd7831d05b5a4acd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020880"
---
# <a name="understanding-backus-nauer-form-bnf-syntax"></a>Comprender la sintaxis de Backus Nauer Form (BNF)

Los scripts usados por el registrador de ATL se describen en este tema mediante la sintaxis BNF, que usa la notación de puntos que se muestra en la tabla siguiente.

|Convención/símbolo|Significado|
|------------------------|-------------|
|::=|Equivalente|
|&#124;|O|
|X +|Xs uno o más.|
|[X]|X es opcional. Los delimitadores opcionales se indican mediante \[].|
|Cualquier **negrita** texto|Un literal de cadena.|
|Cualquier *en cursiva* texto|Cómo construir el literal de cadena.|

Como se indica en la tabla anterior, los scripts del registrador usan literales de cadena. Estos valores son texto real que debe aparecer en el script. En la tabla siguiente se describe los literales de cadena que se usa en un script de registrador de ATL.

|Literal de cadena|Acción|
|--------------------|------------|
|**ForceRemove**|Quita completamente la clave siguiente (si existe) y, a continuación, volver a crearla.|
|**NoRemove**|No quita la clave siguiente durante la eliminación del registro.|
|**Val**|Especifica que `<Key Name>` es realmente un valor con nombre.|
|**Eliminar**|Elimina la clave siguiente durante el registro.|
|**s**|Especifica que el valor siguiente es una cadena (REG_SZ).|
|**d**|Especifica que el valor siguiente es un valor DWORD (REG_DWORD).|
|**m**|Especifica que el valor siguiente es una cadena múltiple (REG_MULTI_SZ).|
|**b**|Especifica que el valor siguiente es un valor binario (REG_BINARY).|

## <a name="bnf-syntax-examples"></a>Ejemplos de sintaxis BNF

Estos son algunos ejemplos de sintaxis que le ayudarán a comprender cómo funcionan los literales de cadena y la notación en un script de registrador de ATL.

### <a name="syntax-example-1"></a>Ejemplo de sintaxis 1

```
<registry expression> ::= <Add Key>
```

Especifica que `registry expression` es equivalente a `Add Key`.

### <a name="syntax-example-2"></a>Ejemplo de sintaxis 2

```
<registry expression> ::= <Add Key> | <Delete Key>
```

Especifica que `registry expression` es equivalente al tipo `Add Key` o `Delete Key`.

### <a name="syntax-example-3"></a>Ejemplo de sintaxis 3

```
<Key Name> ::= '<AlphaNumeric>+'
```

Especifica que `Key Name` equivale a uno o varios `AlphaNumerics`.

### <a name="syntax-example-4"></a>Sintaxis de ejemplo 4

```
<Add Key> ::= [ForceRemove | NoRemove | val]<Key Name>
```

Especifica que `Add Key` es equivalente a `Key Name`y que los literales de cadena, `ForceRemove`, `NoRemove`, y `val`, son opcionales.

### <a name="syntax-example-5"></a>Ejemplo de sintaxis de 5

```
<AlphaNumeric> ::= any character not NULL, that is, ASCII 0
```

Especifica que `AlphaNumeric` es equivalente a cualquier carácter que no es NULL.

### <a name="syntax-example-6"></a>Sintaxis de ejemplo 6

```
val 'testmulti' = m 'String 1\0String 2\0'
```

Especifica que el nombre de clave `testmulti` está formado por un valor multistring `String 1` y `String 2`.

### <a name="syntax-example-7"></a>Ejemplo de sintaxis 7

```
val 'testhex' = d '&H55'
```

Especifica que el nombre de clave `testhex` se establece un valor DWORD a 55 hexadecimal (85 decimal). Tenga en cuenta que este formato se ajusta a la **& H** notación que se encuentra en la especificación de Visual Basic.

## <a name="see-also"></a>Vea también

[Crear scripts del registrador](../atl/creating-registrar-scripts.md)

