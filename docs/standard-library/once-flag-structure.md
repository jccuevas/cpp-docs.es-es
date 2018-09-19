---
title: once_flag (Estructura) | Microsoft Docs
ms.custom: ''
ms.date: 09/17/2018
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
ms.openlocfilehash: 67cfbe06461598fbd04e124629399baa63fdd5d9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104340"
---
# <a name="onceflag-structure"></a>once_flag (Estructura)

Representa un **struct** que se utiliza con la función de plantilla [call_once](../standard-library/mutex-functions.md#call_once) para asegurarse de que la inicialización se llama al código una sola vez, incluso en presencia de varios subprocesos de ejecución.

## <a name="syntax"></a>Sintaxis

estructura once_flag {constexpr once_flag() noexcept;};

## <a name="remarks"></a>Comentarios

El `once_flag` **struct** solo tiene un constructor predeterminado.

Los objetos de tipo `once_flag` pueden crearse, pero no pueden copiarse.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<mutex >

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
