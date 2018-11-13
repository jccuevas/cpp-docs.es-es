---
title: _TRUNCATE
ms.date: 11/04/2016
f1_keywords:
- _TRUNCATE
- TRUNCATE
helpviewer_keywords:
- TRUNCATE constant
- _TRUNCATE constant
ms.assetid: ad093dbf-1aa5-4bd2-9268-efc68afd8434
ms.openlocfilehash: 69dc495083bc7fffd925e42163473c64452cb402
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544266"
---
# <a name="truncate"></a>_TRUNCATE

Especifica el comportamiento de truncamiento de cadenas.

## <a name="syntax"></a>Sintaxis

```
#include <stdlib.h>
```

## <a name="remarks"></a>Comentarios

`_TRUNCATE` habilita el comportamiento de truncamiento cuando se pasa como el parámetro `count` a estas funciones:

[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)

[strncat_s, _strncat_s_l, wcsncat_s, _wcsncat_s_l, _mbsncat_s, _mbsncat_s_l](../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)

[mbstowcs_s, _mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)

[mbsrtowcs_s](../c-runtime-library/reference/mbsrtowcs-s.md)

[wcstombs_s, _wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)

[wcsrtombs_s](../c-runtime-library/reference/wcsrtombs-s.md)

[_snprintf_s, _snprintf_s_l, _snwprintf_s, _snwprintf_s_l](../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)

[vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l](../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)

Si el búfer de destino es demasiado pequeño para contener la cadena completa, el comportamiento normal de estas funciones es considerarlo como una situación de error (consulte [Validación de parámetros](../c-runtime-library/parameter-validation.md)). En cambio, si el truncamiento de cadenas se habilita pasando `_TRUNCATE`, estas funciones solo copiarán la parte de la cadena que quepa, dejando el búfer de destino finalizado en null y se devuelve correctamente.

El truncamiento de cadenas cambia los valores devueltos de las funciones afectadas. Las siguientes funciones devuelven 0 si no se produce ningún truncamiento o `STRUNCATE` si se produce el truncamiento:

[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)

[strncat_s, _strncat_s_l, wcsncat_s, _wcsncat_s_l, _mbsncat_s, _mbsncat_s_l](../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)

[wcstombs_s, _wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)

[mbstowcs_s, _mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)

Las siguientes funciones devuelven el número de caracteres copiados si no se produce ningún truncamiento o -1 si se produce truncamiento (lo que coincide con el comportamiento de las funciones snprintf originales):

[_snprintf_s, _snprintf_s_l, _snwprintf_s, _snwprintf_s_l](../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)

[vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l](../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)

## <a name="example"></a>Ejemplo

```
// crt_truncate.c
#include <stdlib.h>
#include <errno.h>

int main()
{
   char src[] = "1234567890";
   char dst[5];
   errno_t err = strncpy_s(dst, _countof(dst), src, _TRUNCATE);
   if ( err == STRUNCATE )
      printf( "truncation occurred!\n" );
   printf( "'%s'\n", dst );
}
```

```Output
truncation occurred!
'1234'
```

## <a name="see-also"></a>Vea también

[Constantes globales](../c-runtime-library/global-constants.md)