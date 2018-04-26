---
title: mbrtowc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- mbrtowc
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- mbrtowc
dev_langs:
- C++
helpviewer_keywords:
- mbrtowc function
ms.assetid: a1e87fcc-6de0-4ca1-bf26-508d28490286
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a3b567fdbf4cca315efb41e8f331fc2d67830503
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="mbrtowc"></a>mbrtowc

Convierte un carácter multibyte en la configuración regional actual en el carácter ancho equivalente, con capacidad de reinicio en medio de un carácter multibyte.

## <a name="syntax"></a>Sintaxis

```C
size_t mbrtowc(
   wchar_t *wchar,
   const char *mbchar,
   size_t count,
   mbstate_t *mbstate
);
```

### <a name="parameters"></a>Parámetros

*wchar*<br/>
Dirección de un carácter ancho para recibir la cadena de caracteres anchos convertido (tipo **wchar_t**). Este valor puede ser un puntero nulo si no se requiere devolver ningún carácter ancho.

*mbchar*<br/>
Dirección de una secuencia de bytes (un carácter multibyte).

*count*<br/>
Número de bytes que se va a comprobar.

*mbstate*<br/>
Puntero al objeto de estado de la conversión. Si este valor es un puntero nulo, la función utiliza un objeto de estado de la conversión interno estático. Dado que el fax interno **mbstate_t** objeto no es seguro para subprocesos, se recomienda pasar siempre su propio *mbstate* argumento.

## <a name="return-value"></a>Valor devuelto

Uno de los siguientes valores:

0 la próxima *recuento* o menos bytes completan el carácter multibyte que representa el carácter ancho nulo, que se almacena en *wchar*si *wchar* no es un puntero nulo.

1 a *recuento*, ambos inclusive la próxima *recuento* o menos bytes completan un carácter multibyte válido. El valor devuelto es el número de bytes que completan el carácter multibyte. El carácter ancho equivalente se almacena en *wchar*si *wchar* no es un puntero nulo.

(size_t) (-1) Se produjo un error de codificación. La siguiente *recuento* o menos bytes no contribuyen a un carácter multibyte completo y válido. En este caso, **errno** se establece a EILSEQ y el estado de desplazamiento de conversión en *mbstate* no está especificado.

(size_t) -(2) La siguiente *recuento* bytes contribuyen a un carácter multibyte incompleto pero potencialmente válido y los *recuento* bytes se han procesado. Ningún valor se almacena en *wchar*, pero *mbstate* se actualiza para reiniciar la función.

## <a name="remarks"></a>Comentarios

Si *mbchar* es un puntero nulo, la función es equivalente a la llamada:

`mbrtowc(NULL, "", 1, &mbstate)`

En este caso, el valor de los argumentos *wchar* y *recuento* se omiten.

Si *mbchar* no es un puntero nulo, la función examina *recuento* bytes a partir de *mbchar* para determinar el número necesario de bytes que se necesitan para completar la siguiente carácter multibyte. Si el carácter siguiente es válido, el carácter multibyte correspondiente se almacena en *wchar* si no es un puntero nulo. Si el carácter nulo ancho correspondiente no es de carácter, el estado resultante de *mbstate* es el estado inicial de conversión.

El **mbrtowc** función difiere de [mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md) por su capacidad de reinicio. El estado de la conversión se almacena en *mbstate* para llamadas posteriores a la misma o a otras funciones reiniciables. Los resultados no están definidos cuando se combina el uso de funciones reiniciables y no reiniciables.  Por ejemplo, una aplicación debe utilizar **wcsrlen** en lugar de **wcslen** si una llamada subsiguiente a **wcsrtombs** se utiliza en lugar de **wcstombs**.

## <a name="example"></a>Ejemplo

Convierte un carácter multibyte en su equivalente de carácter ancho.

```cpp
// crt_mbrtowc.cpp

#include <stdio.h>
#include <mbctype.h>
#include <string.h>
#include <locale.h>
#include <wchar.h>

#define BUF_SIZE 100

int Sample(char* szIn, wchar_t* wcOut, int nMax)
{
    mbstate_t   state = {0}; // Initial state
    size_t      nConvResult,
                nmbLen = 0,
                nwcLen = 0;
    wchar_t*    wcCur = wcOut;
    wchar_t*    wcEnd = wcCur + nMax;
    const char* mbCur = szIn;
    const char* mbEnd = mbCur + strlen(mbCur) + 1;
    char*       szLocal;

    // Sets all locale to French_Canada.1252
    szLocal = setlocale(LC_ALL, "French_Canada.1252");
    if (!szLocal)
    {
        printf("The fuction setlocale(LC_ALL, \"French_Canada.1252\") failed!\n");
        return 1;
    }

    printf("Locale set to: \"%s\"\n", szLocal);

    // Sets the code page associated current locale's code page
    // from a previous call to setlocale.
    if (_setmbcp(_MB_CP_SBCS) == -1)
    {
        printf("The fuction _setmbcp(_MB_CP_SBCS) failed!");
        return 1;
    }

    while ((mbCur < mbEnd) && (wcCur < wcEnd))
    {
        //
        nConvResult = mbrtowc(wcCur, mbCur, 1, &state);
        switch (nConvResult)
        {
            case 0:
            {  // done
                printf("Conversion succeeded!\nMultibyte String: ");
                printf(szIn);
                printf("\nWC String: ");
                wprintf(wcOut);
                printf("\n");
                mbCur = mbEnd;
                break;
            }

            case -1:
            {  // encoding error
                printf("The call to mbrtowc has detected an encoding error.\n");
                mbCur = mbEnd;
                break;
            }

            case -2:
            {  // incomplete character
                if   (!mbsinit(&state))
                {
                    printf("Currently in middle of mb conversion, state = %x\n", state);
                    // state will contain data regarding lead byte of mb character
                }

                ++nmbLen;
                ++mbCur;
                break;
            }

            default:
            {
                if   (nConvResult > 2) // The multibyte should never be larger than 2
                {
                    printf("Error: The size of the converted multibyte is %d.\n", nConvResult);
                }

                ++nmbLen;
                ++nwcLen;
                ++wcCur;
                ++mbCur;
            break;
            }
        }
    }

   return 0;
}

int main(int argc, char* argv[])
{
    char    mbBuf[BUF_SIZE] = "AaBbCc\x9A\x8B\xE0\xEF\xF0xXyYzZ";
    wchar_t wcBuf[BUF_SIZE] = {L''};

    return Sample(mbBuf, wcBuf, BUF_SIZE);
}
```

### <a name="sample-output"></a>Resultados del ejemplo

```Output
Locale set to: "French_Canada.1252"
Conversion succeeded!
Multibyte String: AaBbCcÜïα∩≡xXyYzZ
WC String: AaBbCcÜïα∩≡xXyYzZ
```

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**mbrtowc**|\<wchar.h>|

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
