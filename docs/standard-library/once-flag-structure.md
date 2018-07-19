---
title: once_flag (Estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- mutex/std::once_flag
dev_langs:
- C++
ms.assetid: 71bfb88d-ca8c-4082-a6e1-ff52151e8629
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f8a8d28f19e32988bfa179642a87e880413bb0ff
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33852343"
---
# <a name="onceflag-structure"></a>once_flag (Estructura)

Representa un `struct` que se usa con la función de plantilla [call_once](../standard-library/mutex-functions.md#call_once) para asegurarse de que solo se llame una vez al código de inicialización, incluso ante la presencia de varios subprocesos de ejecución.

## <a name="syntax"></a>Sintaxis

struct once_flag { constexpr once_flag() noexcept; once_flag(const once_flag&); once_flag& operator=(const once_flag&); };

## <a name="remarks"></a>Comentarios

El `once_flag` `struct` tiene solo un constructor predeterminado.

Los objetos de tipo `once_flag` pueden crearse, pero no pueden copiarse.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<mutex >

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
