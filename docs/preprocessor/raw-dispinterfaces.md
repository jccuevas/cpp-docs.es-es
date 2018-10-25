---
title: raw_dispinterfaces | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_dispinterfaces
dev_langs:
- C++
helpviewer_keywords:
- raw_dispinterfaces attribute
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b89c1f549168a762b5ae095c4eacf5ddb1b4d053
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50062358"
---
# <a name="rawdispinterfaces"></a>raw_dispinterfaces
**Específicos de C++**

Indica al compilador que genere funciones de contenedor de bajo nivel para dispinterface métodos y propiedades que llaman a `IDispatch::Invoke` y devolver el código de error HRESULT.

## <a name="syntax"></a>Sintaxis

```
raw_dispinterfaces
```

## <a name="remarks"></a>Comentarios

Si no se especifica este atributo, solo se generan los contenedores de alto nivel, que inician excepciones de C++ en caso de error.

**FIN de específicos de C++**

## <a name="see-also"></a>Vea también

[atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directiva #import](../preprocessor/hash-import-directive-cpp.md)