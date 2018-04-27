---
title: '&lt;set&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- <set>
dev_langs:
- C++
helpviewer_keywords:
- set header
ms.assetid: 43cb1ab2-6383-48cf-8bdc-2b96d7203596
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8cd38a4a165b3fcd006ef79ec0416a3a32e39dd3
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="ltsetgt"></a>&lt;set&gt;

Define las clases de plantilla de contenedor set y multiset, así como sus plantillas auxiliares.

## <a name="syntax"></a>Sintaxis

```cpp
#include <set>

```

## <a name="members"></a>Miembros

### <a name="operators"></a>Operadores

|Versión set |Versión multiset|Descripción|
|-----------------|----------------------|-----------------|
|[operator!= (set)](../standard-library/set-operators.md#op_neq)|[operator!= (multiset)](../standard-library/set-operators.md#op_neq)|Comprueba si el objeto set o multiset a la izquierda del operador no es igual que el objeto set o multiset situado a la derecha del operador.|
|[operator< (set)](../standard-library/set-operators.md#op_lt)|[operator< (multiset)](../standard-library/set-operators.md#op_lt_multiset)|Comprueba si el objeto set o multiset a la izquierda del operador es menor que el objeto set o multiset situado a la derecha del operador.|
|[operator<= (set)](../standard-library/set-operators.md#op_lt_eq)|[operator\<= (multiset)](../standard-library/set-operators.md#op_lt_eq_multiset)|Comprueba si el objeto set o multiset a la izquierda del operador es menor o igual que el objeto set o multiset situado a la derecha del operador.|
|[operator== (set)](../standard-library/set-operators.md#op_eq_eq)|[operator== (multiset)](../standard-library/set-operators.md#op_eq_eq_multiset)|Comprueba si el objeto set o multiset a la izquierda del operador es igual que el objeto set o multiset situado a la derecha del operador.|
|[operator> (set)](../standard-library/set-operators.md#op_gt)|[operator> (multiset)](../standard-library/set-operators.md#op_gt_multiset)|Comprueba si el objeto set o multiset a la izquierda del operador es mayor que el objeto set o multiset situado a la derecha del operador.|
|[operator>= (set)](../standard-library/set-operators.md#op_gt_eq)|[operator>= (multiset)](../standard-library/set-operators.md#op_gt_eq_multiset)|Comprueba si el objeto set o multiset a la izquierda del operador es mayor o igual que el objeto set o multiset situado a la derecha del operador.|

### <a name="specialized-template-functions"></a>Funciones de plantilla especializadas

|Versión set |Versión multiset|Descripción|
|-----------------|----------------------|-----------------|
|[swap](../standard-library/set-functions.md#swap)|[swap (conjunto mútiple)](../standard-library/set-functions.md#swap_multiset)|Intercambia los elementos de dos sets o multisets.|

### <a name="classes"></a>Clases

|Clase|Descripción|
|-|-|
|[set (Clase)](../standard-library/set-class.md)|Se usa para el almacenamiento y la recuperación de datos de una colección en la que los valores de los elementos contenidos son únicos y sirven como valores de clave según los cuales se ordenan automáticamente los datos.|
|[multiset (Clase)](../standard-library/multiset-class.md)|Se usa para el almacenamiento y la recuperación de datos de una colección en la que los valores de los elementos contenidos no tienen que ser únicos y en la que sirven como valores de clave según los cuales se ordenan automáticamente los datos.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
