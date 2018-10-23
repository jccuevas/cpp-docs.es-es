---
title: inject_statement | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- inject_statement
dev_langs:
- C++
helpviewer_keywords:
- inject_statement attribute
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 27b35c10e9e1953dc45dee1caf61d2e58c38d02d
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808648"
---
# <a name="injectstatement"></a>inject_statement

**Específicos de C++**

Inserta el argumento como texto original en el encabezado de la biblioteca de tipos.

## <a name="syntax"></a>Sintaxis

```
inject_statement("source_text")
```

### <a name="parameters"></a>Parámetros

*source_text*<br/>
Texto original que se inserta en el archivo de encabezado de la biblioteca de tipos.

## <a name="remarks"></a>Comentarios

El texto se coloca al principio de la declaración de espacio de nombres que incluye el contenido de la biblioteca de tipos en el archivo de encabezado.

**FIN de específicos de C++**

## <a name="see-also"></a>Vea también

[atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directiva #import](../preprocessor/hash-import-directive-cpp.md)