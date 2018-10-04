---
title: auto_rename | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- auto_rename
dev_langs:
- C++
helpviewer_keywords:
- auto_rename attribute
ms.assetid: 1075f3ab-f6fc-4e04-8e22-ebe02695a567
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52147dcf79c73e1f931a3e9b52241308def864c4
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2018
ms.locfileid: "48234430"
---
# <a name="autorename"></a>auto_rename

**Específicos de C++**

Cambia de nombre las palabras reservadas de C++ al anexar dos caracteres de subrayado (__) al nombre de la variable para resolver posibles conflictos de nombre.

## <a name="syntax"></a>Sintaxis

```
auto_rename
```

## <a name="remarks"></a>Comentarios

Este atributo se usa al importar una biblioteca de tipos que utiliza una o más palabras reservadas de C++ (palabras clave o macros) como nombres de variable.

**FIN de específicos de C++**

## <a name="see-also"></a>Vea también

[atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directiva #import](../preprocessor/hash-import-directive-cpp.md)