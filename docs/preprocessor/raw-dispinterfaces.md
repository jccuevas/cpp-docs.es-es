---
title: atributo de importación raw_dispinterfaces
ms.date: 08/29/2019
f1_keywords:
- raw_dispinterfaces
helpviewer_keywords:
- raw_dispinterfaces attribute
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
ms.openlocfilehash: 73c58b72b27de8dcf96e8ab9464d0fb6bce12b66
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216228"
---
# <a name="raw_dispinterfaces-import-attribute"></a>atributo de importación raw_dispinterfaces

**C++Cuestión**

Indica al compilador que genere funciones contenedoras de bajo nivel para los métodos dispinterface y para `IDispatch::Invoke` las propiedades que llaman y devuelven el código de error HRESULT.

## <a name="syntax"></a>Sintaxis

> **#import** *biblioteca de tipos* **raw_dispinterfaces**

## <a name="remarks"></a>Comentarios

Si no se especifica este atributo, solo se generan contenedores de alto nivel, que producen C++ excepciones en caso de error.

**Específico C++ de finalización**

## <a name="see-also"></a>Vea también

[atributos de #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import (Directiva)](../preprocessor/hash-import-directive-cpp.md)
