---
title: _kbhit
ms.date: 11/04/2016
api_name:
- _kbhit
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _kbhit
- conio/_kbhit
helpviewer_keywords:
- keyboard input
- user input, checking for keyboard
- kbhit function
- console
- console, checking
- keyboards, keyboard input
- _kbhit function
- keyboards, checking input
ms.assetid: e82a1cc9-bbec-4150-b678-a7e433220fe4
ms.openlocfilehash: 972b060dd98b5d267fa1f529c898573d4b82bb61
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438092"
---
# <a name="_kbhit"></a>_kbhit

Comprueba si hay acciones del teclado en la consola.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C

int _kbhit( void );
```

## <a name="return-value"></a>Valor devuelto

**_kbhit** devuelve un valor distinto de cero si se ha presionado una tecla. De lo contrario, devuelve 0.

## <a name="remarks"></a>Observaciones

La función **_kbhit** comprueba si la consola tiene una pulsación de tecla reciente. Si la función devuelve un valor distinto de cero, hay una pulsación de tecla esperando en el búfer. A continuación, el programa puede llamar a **_getch** o **_getche** para obtener la pulsación de tecla.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_kbhit**|\<conio.h>|

Para más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

```C
// crt_kbhit.c
// compile with: /c
/* This program loops until the user
* presses a key. If _kbhit returns nonzero, a
* keystroke is waiting in the buffer. The program
* can call _getch or _getche to get the keystroke.
*/

#include <conio.h>
#include <stdio.h>

int main( void )
{
   /* Display message until key is pressed. */
   while( !_kbhit() )
      _cputs( "Hit me!! " );

   /* Use _getch to throw key away. */
   printf( "\nKey struck was '%c'\n", _getch() );
}
```

### <a name="sample-output"></a>Salida de ejemplo

```Output
Hit me!! Hit me!! Hit me!! Hit me!! Hit me!! Hit me!! Hit me!!
Key struck was 'q'
```

## <a name="see-also"></a>Consulte también

[E/S de consola y de puerto](../../c-runtime-library/console-and-port-i-o.md)<br/>
