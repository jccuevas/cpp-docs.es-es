---
title: _CrtReportBlockType
ms.date: 11/04/2016
api_name:
- _CrtReportBlockType
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _CrtReportBlockType
- CrtReportBlockType
helpviewer_keywords:
- CrtReportBlockType function
- BLOCK_SUBTYPE macro
- _CrtReportBlockType function
- _BLOCK_TYPE macro
- _BLOCK_SUBTYPE macro
- BLOCK_TYPE macro
ms.assetid: 0f4b9da7-bebb-4956-9541-b2581640ec6b
ms.openlocfilehash: cd50de1d1ade1d83b97bc465ff7e4c73b52fba2d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942341"
---
# <a name="_crtreportblocktype"></a>_CrtReportBlockType

Devuelve el tipo o subtipo de bloque asociado a un puntero de bloque especificado del montón de depuración.

## <a name="syntax"></a>Sintaxis

```C
int _CrtReportBlockType(
   const void * pBlock
};
```

### <a name="parameters"></a>Parámetros

*pBlock*<br/>
Puntero a un bloque válido del montón de depuración.

## <a name="return-value"></a>Valor devuelto

Cuando se pasa un puntero de montón de depuración válido, la función **_CrtReportBlockType** devuelve el tipo de bloque y el subtipo en forma de **int**. Cuando se le pasa un puntero no válido, la función devuelve -1.

## <a name="remarks"></a>Comentarios

Para extraer el tipo y el subtipo devueltos por **_CrtReportBlockType**, use las macros **_BLOCK_TYPE** y **_BLOCK_SUBTYPE** (ambas definidas en CRTDBG. h) en el valor devuelto.

Para obtener información sobre la asignación de tipos de bloque y cómo se usan, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_CrtReportBlockType**|\<crtdbg.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

```cpp
// crt_crtreportblocktype.cpp
// compile with: /MDd

#include <malloc.h>
#include <stdio.h>
#include <crtdbg.h>

void __cdecl Dumper(void *ptr, void *)
{
    int block = _CrtReportBlockType(ptr);
    _RPT3(_CRT_WARN, "Dumper found block at %p: type %d, subtype %d\n", ptr,
          _BLOCK_TYPE(block), _BLOCK_SUBTYPE(block));
}

void __cdecl LeakDumper(void *ptr, size_t sz)
{
    int block = _CrtReportBlockType(ptr);
    _RPT4(_CRT_WARN, "LeakDumper found block at %p:"
                     " type %d, subtype %d, size %d\n", ptr,
          _BLOCK_TYPE(block), _BLOCK_SUBTYPE(block), sz);
}

int main(void)
{
    _CrtSetDbgFlag(_CrtSetDbgFlag(_CRTDBG_REPORT_FLAG) |
    _CRTDBG_LEAK_CHECK_DF);
    _CrtSetReportMode( _CRT_WARN, _CRTDBG_MODE_FILE );
    _CrtSetReportFile( _CRT_WARN, _CRTDBG_FILE_STDOUT );
    _malloc_dbg(10, _NORMAL_BLOCK , __FILE__, __LINE__);
    _malloc_dbg(10, _CLIENT_BLOCK | (1 << 16), __FILE__, __LINE__);
    _malloc_dbg(20, _CLIENT_BLOCK | (2 << 16), __FILE__, __LINE__);
    _malloc_dbg(30, _CLIENT_BLOCK | (3 << 16), __FILE__, __LINE__);
    _CrtDoForAllClientObjects(Dumper, NULL);
    _CrtSetDumpClient(LeakDumper);
}
```

### <a name="sample-output"></a>Resultados del ejemplo

```Output
Dumper found block at 00314F78: type 4, subtype 3
Dumper found block at 00314F38: type 4, subtype 2
Dumper found block at 00314F00: type 4, subtype 1
Detected memory leaks!
Dumping objects ->
crt_crtreportblocktype.cpp(30) : {55} client block at 0x00314F78, subtype 3, 30 bytes long.
Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
crt_crtreportblocktype.cpp(29) : {54} client block at 0x00314F38, subtype 2, 20 bytes long.
Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
crt_crtreportblocktype.cpp(28) : {53} client block at 0x00314F00, subtype 1, 10 bytes long.
Data: <          > CD CD CD CD CD CD CD CD CD CD
crt_crtreportblocktype.cpp(27) : {52} normal block at 0x00314EC8, 10 bytes long.
Data: <          > CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

## <a name="see-also"></a>Vea también

[_CrtDoForAllClientObjects](crtdoforallclientobjects.md)<br/>
[_CrtSetDumpClient](crtsetdumpclient.md)<br/>
[_CrtMemDumpAllObjectsSince](crtmemdumpallobjectssince.md)<br/>
[_CrtDumpMemoryLeaks](crtdumpmemoryleaks.md)<br/>
