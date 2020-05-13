---
title: setbuf
ms.date: 4/2/2020
api_name:
- setbuf
- _o_setbuf
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- setbuf
helpviewer_keywords:
- setbuf function
- stream buffering
ms.assetid: 13beda22-7b56-455d-8a6c-f2eb636885b9
ms.openlocfilehash: 40f23db88abf9733eada9e775aacda83cba5829a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910332"
---
# <a name="setbuf"></a>setbuf

Controla el almacenamiento en búfer de la secuencia. Esta función está en desuso; use [setvbuf](setvbuf.md) en su lugar.

## <a name="syntax"></a>Sintaxis

```C
void setbuf(
   FILE *stream,
   char *buffer
);
```

### <a name="parameters"></a>Parámetros

*misiones*<br/>
Puntero a la estructura **FILE**.

*búfer*<br/>
Búfer asignado por el usuario.

## <a name="remarks"></a>Observaciones

La función **setbuf** controla el almacenamiento en búfer de la *secuencia*. El argumento de *secuencia* debe hacer referencia a un archivo abierto que no se ha leído o escrito. Si el argumento de *búfer* es **null**, el flujo no se almacena en búfer. De lo contrario, el búfer debe apuntar a una matriz de caracteres de longitud **BUFSIZ**, donde **BUFSIZ** es el tamaño del búfer tal y como se define en stdio. C. Para el almacenamiento en búfer de E/S se usa el búfer especificado por el usuario, y no el búfer predeterminado asignado por el sistema para la secuencia especificada. La secuencia **stderr** no se almacena en búfer de forma predeterminada, pero puede usar **setbuf** para asignar búferes a **stderr**.

**setbuf** se ha reemplazado por [setvbuf (](setvbuf.md), que es la rutina preferida para el nuevo código. A diferencia de **setvbuf (**, **setbuf** no tiene forma de generar informes de errores. **setvbuf (** también le permite controlar el modo de almacenamiento en búfer y el tamaño del búfer. **setbuf** existe por compatibilidad con el código existente.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**setbuf**|\<stdio.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_setbuf.c
// compile with: /W3
// This program first opens files named DATA1 and
// DATA2. Then it uses setbuf to give DATA1 a user-assigned
// buffer and to change DATA2 so that it has no buffer.

#include <stdio.h>

int main( void )
{
   char buf[BUFSIZ];
   FILE *stream1, *stream2;

   fopen_s( &stream1, "data1", "a" );
   fopen_s( &stream2, "data2", "w" );

   if( (stream1 != NULL) && (stream2 != NULL) )
   {
      // "stream1" uses user-assigned buffer:
      setbuf( stream1, buf ); // C4996
      // Note: setbuf is deprecated; consider using setvbuf instead
      printf( "stream1 set to user-defined buffer at: %Fp\n", buf );

      // "stream2" is unbuffered
      setbuf( stream2, NULL ); // C4996
      printf( "stream2 buffering disabled\n" );
      _fcloseall();
   }
}
```

```Output
stream1 set to user-defined buffer at: 0012FCDC
stream2 buffering disabled
```

## <a name="see-also"></a>Consulte también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[setvbuf](setvbuf.md)<br/>
