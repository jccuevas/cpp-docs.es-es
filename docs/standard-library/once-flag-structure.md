---
title: once_flag (Estructura)
ms.date: 09/17/2018
f1_keywords:
- mutex/std::once_flag
ms.assetid: 71bfb88d-ca8c-4082-a6e1-ff52151e8629
ms.openlocfilehash: 004a5545e2eccab83b0846e2ae30b88c8431c99d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62371443"
---
# <a name="onceflag-structure"></a>once_flag (Estructura)

Representa un **struct** que se utiliza con la función de plantilla [call_once](../standard-library/mutex-functions.md#call_once) para asegurarse de que la inicialización se llama al código una sola vez, incluso en presencia de varios subprocesos de ejecución.

## <a name="syntax"></a>Sintaxis

struct once_flag { constexpr once_flag() noexcept; };

## <a name="remarks"></a>Comentarios

El `once_flag` **struct** solo tiene un constructor predeterminado.

Los objetos de tipo `once_flag` pueden crearse, pero no pueden copiarse.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<mutex >

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
