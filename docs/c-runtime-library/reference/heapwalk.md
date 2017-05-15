---
title: _heapwalk | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _heapwalk
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- heapwalk
- _heapwalk
dev_langs:
- C++
helpviewer_keywords:
- debugging [CRT], heap-related problems
- heapwalk function
- _heapwalk function
ms.assetid: 2df67649-fb00-4570-a8b1-a4eca5738744
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 936ca2f3f4e4f2fb57dd730f5a58927d08d6207f
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="heapwalk"></a>_heapwalk
Recorre el montón y devuelve información sobre la entrada siguiente.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows Runtime, salvo en compilaciones Debug. Para más información, vea [Funciones de CRT no admitidas con /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _heapwalk(   
   _HEAPINFO *entryinfo   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `entryinfo`  
 Búfer que contendrá la información del montón.  
  
## <a name="return-value"></a>Valor devuelto  
 `_heapwalk` devuelve una de las siguientes constantes de manifiesto enteras, definidas en Malloc.h.  
  
 `_HEAPBADBEGIN`  
 La información de encabezado inicial no es válida o no se encuentra.  
  
 `_HEAPBADNODE`  
 Se ha encontrado un montón dañado o un nodo incorrecto.  
  
 `_HEAPBADPTR`  
El campo  `_pentry` de la estructura de `_HEAPINFO` no contiene un puntero válido para el montón o `entryinfo` es un puntero nulo.  
  
 `_HEAPEND`  
 Se ha llegado al final del montón correctamente.  
  
 `_HEAPEMPTY`  
 El montón no está inicializado.  
  
 `_HEAPOK`  
 Ningún error hasta el momento. `entryinfo` se actualiza con la información sobre la siguiente entrada del montón.  
  
 Además, si se produce un error, `_heapwalk` establece `errno` en `ENOSYS`.  
  
## <a name="remarks"></a>Comentarios  
 La función `_heapwalk` ayuda a depurar problemas relacionados con el montón de los programas. La función recorre el montón, atravesando una entrada por llamada, y devuelve un puntero a una estructura del tipo `_HEAPINFO` que contiene información sobre la siguiente entrada del montón. El tipo `_HEAPINFO`, definido en Malloc.h, contiene los elementos siguientes.  
  
 `int *_pentry`  
 Puntero de entrada en el montón.  
  
 `size_t _size`  
 Tamaño de la entrada del montón.  
  
 `int _useflag`  
 Marca que indica si la entrada del montón está en uso.  
  
 Una llamada a `_heapwalk` que devuelve `_HEAPOK` almacena el tamaño de la entrada en el campo `_size` y establece el campo `_useflag` en `_FREEENTRY` o `_USEDENTRY` (ambas constantes se definen en Malloc.h). Para obtener esta información sobre la primera entrada del montón, pase un puntero de `_heapwalk` a una estructura de `_HEAPINFO` cuyo miembro `_pentry` sea `NULL`. Si el sistema operativo no admite `_heapwalk` (por ejemplo, Windows 98), la función devuelve `_HEAPEND` y establece `errno` en `ENOSYS`.  
  
 Esta función valida su parámetro. Si `entryinfo` es un puntero nulo, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, `errno` se establece en `EINVAL` y la función devuelve `_HEAPBADPTR`.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|-------------|---------------------|---------------------|  
|`_heapwalk`|\<malloc.h>|\<errno.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_heapwalk.c  
  
// This program "walks" the heap, starting  
// at the beginning (_pentry = NULL). It prints out each  
// heap entry's use, location, and size. It also prints  
// out information about the overall state of the heap as  
// soon as _heapwalk returns a value other than _HEAPOK  
// or if the loop has iterated 100 times.  
  
#include <stdio.h>  
#include <malloc.h>  
  
void heapdump(void);  
  
int main(void)  
{  
    char *buffer;  
  
    heapdump();  
    if((buffer = (char *)malloc(59)) != NULL)  
    {  
        heapdump();  
        free(buffer);  
    }  
    heapdump();  
}  
  
void heapdump(void)  
{  
    _HEAPINFO hinfo;  
    int heapstatus;  
    int numLoops;  
    hinfo._pentry = NULL;  
    numLoops = 0;  
    while((heapstatus = _heapwalk(&hinfo)) == _HEAPOK &&  
          numLoops < 100)  
    {  
        printf("%6s block at %Fp of size %4.4X\n",  
               (hinfo._useflag == _USEDENTRY ? "USED" : "FREE"),  
               hinfo._pentry, hinfo._size);  
        numLoops++;  
    }  
  
    switch(heapstatus)  
    {  
    case _HEAPEMPTY:  
        printf("OK - empty heap\n");  
        break;  
    case _HEAPEND:  
        printf("OK - end of heap\n");  
        break;  
    case _HEAPBADPTR:  
        printf("ERROR - bad pointer to heap\n");  
        break;  
    case _HEAPBADBEGIN:  
        printf("ERROR - bad start of heap\n");  
        break;  
    case _HEAPBADNODE:  
        printf("ERROR - bad node in heap\n");  
        break;  
    }  
}  
```  
  
```Output  
  USED block at 00310650 of size 0100  
  USED block at 00310758 of size 0800  
  USED block at 00310F60 of size 0080  
  FREE block at 00310FF0 of size 0398  
  USED block at 00311390 of size 000D  
  USED block at 003113A8 of size 00B4  
  USED block at 00311468 of size 0034  
  USED block at 003114A8 of size 0039  
...  
  USED block at 00312228 of size 0010  
  USED block at 00312240 of size 1000  
  FREE block at 00313250 of size 1DB0  
OK - end of heap  
```  
  
## <a name="see-also"></a>Vea también  
 [Asignación de memoria](../../c-runtime-library/memory-allocation.md)   
 [_heapadd](../../c-runtime-library/heapadd.md)   
 [_heapchk](../../c-runtime-library/reference/heapchk.md)   
 [_heapmin](../../c-runtime-library/reference/heapmin.md)   
 [_heapset](../../c-runtime-library/heapset.md)
