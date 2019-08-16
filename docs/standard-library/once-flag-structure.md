---
title: once_flag (Estructura)
ms.date: 09/17/2018
f1_keywords:
- mutex/std::once_flag
ms.assetid: 71bfb88d-ca8c-4082-a6e1-ff52151e8629
ms.openlocfilehash: fb85bd48f9b1ac10ec2fefbc6738aae777f67bcf
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455208"
---
# <a name="onceflag-structure"></a>once_flag (Estructura)

Representa un **struct** que se usa con la función de plantilla [call_once](../standard-library/mutex-functions.md#call_once) para garantizar que solo se llame una vez al código de inicialización, incluso en presencia de varios subprocesos de ejecución.

## <a name="syntax"></a>Sintaxis

struct once_flag { constexpr once_flag() noexcept; };

## <a name="remarks"></a>Comentarios

El `once_flag` **struct** solo tiene un constructor predeterminado.

Los objetos de tipo `once_flag` pueden crearse, pero no pueden copiarse.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<exclusión mutua >

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
