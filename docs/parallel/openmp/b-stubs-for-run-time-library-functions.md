---
title: B. Códigos auxiliares para funciones de biblioteca en tiempo de ejecución
ms.date: 01/22/2019
ms.assetid: fdfdabe0-f678-4551-80d5-827b62354427
ms.openlocfilehash: 9089bd6ef1f0a8f2f2ed94a7c496943c9bdd5e64
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215064"
---
# <a name="b-stubs-for-run-time-library-functions"></a>B. Códigos auxiliares para funciones de biblioteca en tiempo de ejecución

En esta sección se proporcionan códigos auxiliares para las funciones de la biblioteca en tiempo de ejecución C++ definidas en la API y C de OpenMP. Los códigos auxiliares se proporcionan para habilitar la portabilidad a las plataformas que no admiten C++ la API y C de OpenMP. En estas plataformas, los programas de OpenMP deben estar vinculados con una biblioteca que contenga estas funciones de código auxiliar. Las funciones de código auxiliar suponen que se omiten las directivas del programa OpenMP. Como tal, emulan la semántica en serie.

> [!NOTE]
> Se debe tener acceso a la variable de bloqueo que aparece en las funciones de bloqueo exclusivamente a través de estas funciones. No debe inicializarse ni modificarse en el programa del usuario. Los usuarios no deben realizar suposiciones sobre los mecanismos utilizados por las C++ implementaciones de OpenMP C y para implementar bloqueos basados en el esquema utilizado por las funciones de código auxiliar.

## <a name="code"></a>Código

```cpp
#include <stdio.h>
#include <stdlib.h>
#include "omp.h"
#ifdef __cplusplus
extern "C" {
#endif

void omp_set_num_threads(int num_threads)
{
}
int omp_get_num_threads(void)
{
    return 1;
}
int omp_get_max_threads(void)
{
    return 1;
}
int omp_get_thread_num(void)
{
    return 0;
}
int omp_get_num_procs(void)
{
    return 1;
}
void omp_set_dynamic(int dynamic_threads)
{
}
int omp_get_dynamic(void)
{
    return 0;
}
int omp_in_parallel(void)
{
    return 0;
}
void omp_set_nested(int nested)
{
}
int omp_get_nested(void)
{
    return 0;
}
enum {UNLOCKED = -1, INIT, LOCKED};
void omp_init_lock(omp_lock_t *lock)
{
    *lock = UNLOCKED;
}
void omp_destroy_lock(omp_lock_t *lock)
{
    *lock = INIT;
}
void omp_set_lock(omp_lock_t *lock)
{
    if (*lock == UNLOCKED)
    {
        *lock = LOCKED;
    }
    else
        if (*lock == LOCKED)
        {
         fprintf_s(stderr, "error: deadlock in using lock variable\n");
         exit(1);
        } else {
         fprintf_s(stderr, "error: lock not initialized\n");
         exit(1);
        }
}

void omp_unset_lock(omp_lock_t *lock)
{
    if (*lock == LOCKED)
    {
        *lock = UNLOCKED;
    }
    else
        if (*lock == UNLOCKED)
        {
            fprintf_s(stderr, "error: lock not set\n");
            exit(1);
        } else {
            fprintf_s(stderr, "error: lock not initialized\n");
            exit(1);
        }
}

int omp_test_lock(omp_lock_t *lock)
{
    if (*lock == UNLOCKED)
    {
        *lock = LOCKED;
        return 1;
    } else if (*lock == LOCKED) {
        return 0;
    } else {
        fprintf_s(stderr, "error: lock not initialized\n");
        exit(1);
    }
}

#ifndef OMP_NEST_LOCK_T
typedef struct {  // This really belongs in omp.h
    int owner;
    int count;
} omp_nest_lock_t;
#endif
enum {MASTER = 0};
void omp_init_nest_lock(omp_nest_lock_t *lock)
{
    lock->owner = UNLOCKED;
    lock->count = 0;
}
void omp_destroy_nest_lock(omp_nest_lock_t *lock)
{
    lock->owner = UNLOCKED;
    lock->count = UNLOCKED;
}

void omp_set_nest_lock(omp_nest_lock_t *lock)
{
    if (lock->owner == MASTER && lock->count >= 1)
    {
        lock->count++;
    } else
        if (lock->owner == UNLOCKED && lock->count == 0)
        {
            lock->owner = MASTER;
            lock->count = 1;
        } else
        {
       fprintf_s(stderr, "error: lock corrupted or not initialized\n");
         exit(1);
    }
}

void omp_unset_nest_lock(omp_nest_lock_t *lock)
{
    if (lock->owner == MASTER && lock->count >= 1)
    {
        lock->count--;
        if (lock->count == 0)
        {
            lock->owner = UNLOCKED;
        }
    } else
        if (lock->owner == UNLOCKED && lock->count == 0)
        {
            fprintf_s(stderr, "error: lock not set\n");
            exit(1);
        } else
        {
       fprintf_s(stderr, "error: lock corrupted or not initialized\n");
       exit(1);
    }
}

int omp_test_nest_lock(omp_nest_lock_t *lock)
{
    omp_set_nest_lock(lock);
    return lock->count;
}

double omp_get_wtime(void)
{
    // This function does not provide a working
    // wallclock timer. Replace it with a version
    // customized for the target machine.
    return 0.0;
}

double omp_get_wtick(void)
{
    // This function does not provide a working
    // clock tick function. Replace it with
    // a version customized for the target machine.
    return 365. * 86400.;
}

#ifdef __cplusplus
}
#endif
```
