---
title: A.25 ejemplos de la cláusula de atributos de datos copyprivate | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 7b1cb6a5-5691-4b95-b3ac-d7543ede6405
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 95d68c445c1c20e97725d869061027a9712c2462
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413647"
---
# <a name="a25---examples-of-the-copyprivate-data-attribute-clause"></a>A.25 Ejemplos de la cláusula de atributos de datos copyprivate

**Ejemplo 1:** el `copyprivate` cláusula ([sección 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md) en la página 32) puede usarse para difundir valores adquiridos por un único subproceso directamente a todas las instancias de las variables privadas de los demás subprocesos.

```
float x, y;
#pragma omp threadprivate(x, y)

void init( )
{
    float a;
    float b;

    #pragma omp single copyprivate(a,b,x,y)
    {
        get_values(a,b,x,y);
    }

    use_values(a, b, x, y);
}
```

Si la rutina *init* se llama desde una región de la serie, su comportamiento no resulta afectado por la presencia de las directivas. Después de llamar a la *get_values* rutina se ha ejecutado por un subproceso, no hay ningún subproceso deja la construcción hasta que los objetos privados designados por *un*, *b*, *x*, y *y* en todos los subprocesos se convierten en ha definido con los valores leídos.

**Ejemplo 2:** a diferencia del ejemplo anterior, suponga que un subproceso determinado, por ejemplo el subproceso principal debe realizar la operación de lectura. En este caso, el `copyprivate` cláusula no puede utilizarse para realizar la difusión directamente, pero se puede usar para proporcionar acceso a un objeto temporal compartido.

```
float read_next( )
{
    float * tmp;
    float return_val;

    #pragma omp single copyprivate(tmp)
    {
        tmp = (float *) malloc(sizeof(float));
    }

    #pragma omp master
    {
        get_float( tmp );
    }

    #pragma omp barrier
    return_val = *tmp;
    #pragma omp barrier

    #pragma omp single
    {
       free(tmp);
    }

    return return_val;
}
```

**Ejemplo 3:** suponga que el número de objetos de bloqueo necesarios dentro de una región paralela no puede determinarse fácilmente antes de especificarlo. El `copyprivate` cláusula puede usarse para proporcionar acceso a objetos de bloqueo compartido que se asignan dentro de esa región paralela.

```
#include <omp.h>

omp_lock_t *new_lock()
{
    omp_lock_t *lock_ptr;

    #pragma omp single copyprivate(lock_ptr)
    {
        lock_ptr = (omp_lock_t *) malloc(sizeof(omp_lock_t));
        omp_init_lock( lock_ptr );
    }

    return lock_ptr;
}
```