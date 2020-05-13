---
title: Clase CStringT
ms.date: 03/27/2019
f1_keywords:
- CStringT
- ATLSTR/ATL::CStringT
- ATLSTR/ATL::CStringT::CStringT
- ATLSTR/ATL::CStringT::AllocSysString
- ATLSTR/ATL::CStringT::AnsiToOem
- ATLSTR/ATL::CStringT::AppendFormat
- ATLSTR/ATL::CStringT::Collate
- ATLSTR/ATL::CStringT::CollateNoCase
- ATLSTR/ATL::CStringT::Compare
- ATLSTR/ATL::CStringT::CompareNoCase
- ATLSTR/ATL::CStringT::Delete
- ATLSTR/ATL::CStringT::Find
- ATLSTR/ATL::CStringT::FindOneOf
- ATLSTR/ATL::CStringT::Format
- ATLSTR/ATL::CStringT::FormatMessage
- ATLSTR/ATL::CStringT::FormatMessageV
- ATLSTR/ATL::CStringT::FormatV
- ATLSTR/ATL::CStringT::GetEnvironmentVariable
- ATLSTR/ATL::CStringT::Insert
- ATLSTR/ATL::CStringT::Left
- ATLSTR/ATL::CStringT::LoadString
- ATLSTR/ATL::CStringT::MakeLower
- ATLSTR/ATL::CStringT::MakeReverse
- ATLSTR/ATL::CStringT::MakeUpper
- ATLSTR/ATL::CStringT::Mid
- ATLSTR/ATL::CStringT::OemToAnsi
- ATLSTR/ATL::CStringT::Remove
- ATLSTR/ATL::CStringT::Replace
- ATLSTR/ATL::CStringT::ReverseFind
- ATLSTR/ATL::CStringT::Right
- ATLSTR/ATL::CStringT::SetSysString
- ATLSTR/ATL::CStringT::SpanExcluding
- ATLSTR/ATL::CStringT::SpanIncluding
- ATLSTR/ATL::CStringT::Tokenize
- ATLSTR/ATL::CStringT::Trim
- ATLSTR/ATL::CStringT::TrimLeft
- ATLSTR/ATL::CStringT::TrimRight
- CSTRINGT/CStringT
- CSTRINGT/CStringT::CStringT
- CSTRINGT/CStringT::AllocSysString
- CSTRINGT/CStringT::AnsiToOem
- CSTRINGT/CStringT::AppendFormat
- CSTRINGT/CStringT::Collate
- CSTRINGT/CStringT::CollateNoCase
- CSTRINGT/CStringT::Compare
- CSTRINGT/CStringT::CompareNoCase
- CSTRINGT/CStringT::Delete
- CSTRINGT/CStringT::Find
- CSTRINGT/CStringT::FindOneOf
- CSTRINGT/CStringT::Format
- CSTRINGT/CStringT::FormatMessage
- CSTRINGT/CStringT::FormatMessageV
- CSTRINGT/CStringT::FormatV
- CSTRINGT/CStringT::GetEnvironmentVariable
- CSTRINGT/CStringT::Insert
- CSTRINGT/CStringT::Left
- CSTRINGT/CStringT::LoadString
- CSTRINGT/CStringT::MakeLower
- CSTRINGT/CStringT::MakeReverse
- CSTRINGT/CStringT::MakeUpper
- CSTRINGT/CStringT::Mid
- CSTRINGT/CStringT::OemToAnsi
- CSTRINGT/CStringT::Remove
- CSTRINGT/CStringT::Replace
- CSTRINGT/CStringT::ReverseFind
- CSTRINGT/CStringT::Right
- CSTRINGT/CStringT::SetSysString
- CSTRINGT/CStringT::SpanExcluding
- CSTRINGT/CStringT::SpanIncluding
- CSTRINGT/CStringT::Tokenize
- CSTRINGT/CStringT::Trim
- CSTRINGT/CStringT::TrimLeft
- CSTRINGT/CStringT::TrimRight
helpviewer_keywords:
- strings [C++], in ATL
- shared classes, CStringT
- CStringT class
ms.assetid: 7cacc59c-425f-40f1-8f5b-6db921318ec9
ms.openlocfilehash: 8fcce4c426cd99785d34dc080f238cc78cdfee36
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746713"
---
# <a name="cstringt-class"></a>Clase CStringT

Esta clase representa `CStringT` un objeto.

## <a name="syntax"></a>Sintaxis

```
template<typename BaseType, class StringTraits>
class CStringT :
    public CSimpleStringT<BaseType,
        _CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>::c_bIsMFCDLLTraits>
```

#### <a name="parameters"></a>Parámetros

*BaseType*<br/>
El tipo de carácter de la clase de cadena. Puede ser uno de los siguientes:

- **char** (para cadenas de caracteres ANSI).

- **wchar_t** (para cadenas de caracteres Unicode).

- TCHAR (para cadenas de caracteres ANSI y Unicode).

*StringTraits*<br/>
Determina si la clase de cadena necesita compatibilidad con la biblioteca de tiempo de ejecución de C (CRT) y dónde se encuentran los recursos de cadena. Puede ser uno de los siguientes:

- **StrTraitATL< wchar_t &#124;** **char** &#124; **TCHAR, ChTraitsCRT< wchar_t &#124;** **char** &#124; **TCHAR > >**

   La clase requiere compatibilidad con CRT y busca cadenas `m_hInstResource` de recursos en el módulo especificado por (un miembro de la clase de módulo de la aplicación).

- **StrTraitATL< wchar_t<** **&#124;** &#124; **TCHAR, ChTraitsOS< wchar_t &#124;** **&#124;** ** > >TCHAR**

   La clase no requiere compatibilidad con CRT y busca cadenas `m_hInstResource` de recursos en el módulo especificado por (un miembro de la clase de módulo de la aplicación).

- **StrTraitMFC< wchar_t &#124;** **char** &#124; **TCHAR, ChTraitsCRT< wchar_t** **&#124;** > >tCHAR &#124; **tCHAR** de<

   La clase requiere compatibilidad con CRT y busca cadenas de recursos mediante el algoritmo de búsqueda MFC estándar.

- **StrTraitMFC< wchar_t &#124;** **&#124;** **TCHAR, ChTraitsOS< wchar_t** &#124; tchar &#124; **tCHAR > >** **char**

   La clase no requiere compatibilidad con CRT y busca cadenas de recursos mediante el algoritmo de búsqueda ESTÁNDAR de MFC.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CStringT::CStringT](#cstringt)|Construye un `CStringT` objeto de varias maneras.|
|[CStringT::-CStringT](#_dtorcstringt)|Destruye un objeto `CStringT` .|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CStringT::AllocSysString](#allocsysstring)|Asigna un BSTR `CStringT` a partir de datos.|
|[CStringT::AnsiToOem](#ansitooem)|Realiza una conversión in situ del juego de caracteres ANSI al juego de caracteres OEM.|
|[CStringT::AppendFormat](#appendformat)|Anexa datos con formato `CStringT` a un objeto existente.|
|[CStringT::Collate](#collate)|Compara dos cadenas (distingue mayúsculas de minúsculas, utiliza información específica de la configuración regional).|
|[CStringT::CollateNoCase](#collatenocase)|Compara dos cadenas (sin distinción entre mayúsculas y minúsculas, utiliza información específica de la configuración regional).|
|[CStringT::Compare](#compare)|Compara dos cadenas (con distinción entre mayúsculas y minúsculas).|
|[CStringT::CompareNoCase](#comparenocase)|Compara dos cadenas (sin distinción entre mayúsculas y minúsculas).|
|[CStringT::Delete](#delete)|Elimina un carácter o caracteres de una cadena.|
|[CStringT::Buscar](#find)|Busca un carácter o subcadena dentro de una cadena más grande.|
|[CStringT::FindoneOf](#findoneof)|Busca el primer carácter coincidente de un conjunto.|
|[CStringT::Formato](#format)|Da formato `sprintf` a la cadena como lo hace.|
|[CStringT::FormatMessage](#formatmessage)|Da formato a una cadena de mensaje.|
|[CStringT::FormatMessageV](#formatmessagev)|Da formato a una cadena de mensaje mediante una lista de argumentos de variable.|
|[CStringT::FormatV](#formatv)|Da formato a la cadena mediante una lista de variables de argumentos.|
|[CStringT::GetEnvironmentVariable](#getenvironmentvariable)|Establece la cadena en el valor de la variable de entorno especificada.|
|[CStringT::Insertar](#insert)|Inserta un solo carácter o una subcadena en el índice especificado dentro de la cadena.|
|[CStringT::Izquierda](#left)|Extrae la parte izquierda de una cadena.|
|[CStringT::LoadString](#loadstring)|Carga un `CStringT` objeto existente desde un recurso de Windows.|
|[CStringT::MakeLower](#makelower)|Convierte todos los caracteres de esta cadena en caracteres en minúsculas.|
|[CStringT::MakeReverse](#makereverse)|Invierte la cadena.|
|[CStringT::MakeUpper](#makeupper)|Convierte todos los caracteres de esta cadena en caracteres en mayúsculas.|
|[CStringT::Mid](#mid)|Extrae la parte central de una cadena.|
|[CStringT::OemToAnsi](#oemtoansi)|Realiza una conversión in situ del juego de caracteres OEM al juego de caracteres ANSI.|
|[CStringT::Quitar](#remove)|Quita los caracteres indicados de una cadena.|
|[CStringT::Reemplazar](#replace)|Reemplaza los caracteres indicados por otros caracteres.|
|[CStringT::ReverseFind](#reversefind)|Busca un carácter dentro de una cadena más grande; comienza desde el final.|
|[CStringT::Right](#right)|Extrae la parte derecha de una cadena.|
|[CStringT::SetSysString](#setsysstring)|Establece un objeto BSTR existente `CStringT` con datos de un objeto.|
|[CStringT::SpanExcluding](#spanexcluding)|Extrae caracteres de la cadena, empezando por el primer carácter, que no están en el conjunto de caracteres identificados por `pszCharSet`.|
|[CStringT::SpanIncluding](#spanincluding)|Extrae una subcadena que contiene solo los caracteres de un conjunto.|
|[CStringT::Tokenize](#tokenize)|Extrae los tokens especificados en una cadena de destino.|
|[CStringT::Trim](#trim)|Recorta todos los caracteres de espacio en blanco iniciales y finales de la cadena.|
|[CStringT::TrimLeft](#trimleft)|Recorta los caracteres de espacio en blanco iniciales de la cadena.|
|[CStringt::TrimRight](#trimright)|Recorta los caracteres de espacio en blanco finales de la cadena.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[CStringT::operador ?](#operator_eq)|Asigna un nuevo valor `CStringT` a un objeto.|
|[CStringT::operador +](#operator_add)|Concatena dos cadenas o un carácter y una cadena.|
|[CStringT::operador +o](#operator_add_eq)|Concatena una nueva cadena hasta el final de una cadena existente.|
|[CStringT::operador ?](#operator_eq_eq)|Determina si dos cadenas son lógicamente iguales.|
|[CStringT::operador !-](#operator_neq)|Determina si dos cadenas lógicamente no son iguales.|
|[CStringT::operator&lt;](#operator_lt)|Determina si la cadena en el lado izquierdo del operador es menor que a la cadena en el lado derecho.|
|[CStringT::operator&gt;](#operator_gt)|Determina si la cadena en el lado izquierdo del operador es mayor que la cadena en el lado derecho.|
|[CStringT::operator&lt;=](#operator_lt_eq)|Determina si la cadena en el lado izquierdo del operador es menor o igual que la cadena en el lado derecho.|
|[CStringT::operator&gt;=](#operator_gt_eq)|Determina si la cadena en el lado izquierdo del operador es mayor o igual que la cadena en el lado derecho.|

## <a name="remarks"></a>Observaciones

`CStringT`hereda de [CSimpleStringT (Clase).](../../atl-mfc-shared/reference/csimplestringt-class.md) Las características avanzadas, como la manipulación de `CStringT`caracteres, el orden y la búsqueda, se implementan mediante .

> [!NOTE]
> `CStringT`objetos son capaces de producir excepciones. Esto ocurre `CStringT` cuando un objeto se queda sin memoria por cualquier motivo.

Un `CStringT` objeto consta de una secuencia de caracteres de longitud variable. `CStringT`proporciona funciones y operadores utilizando una sintaxis similar a la de Basic. Los operadores de concatenación y comparación, junto con la administración de memoria simplificada, hacen que `CStringT` los objetos sean más fáciles de usar que las matrices de caracteres normales.

> [!NOTE]
> Aunque es posible `CStringT` crear instancias que contengan caracteres nulos incrustados, se recomienda en su contra. Llamar a métodos y operadores en `CStringT` objetos que contienen caracteres nulos incrustados puede producir resultados no deseados.

Mediante el uso de `BaseType` `StringTraits` diferentes `CStringT` combinaciones de los parámetros y, los objetos pueden venir en los siguientes tipos, que han sido predefinidos por las bibliotecas ATL.

Si se utiliza en una aplicación ATL:

`CString`, `CStringA`, `CStringW` y se exportan desde el archivo DLL de MFC (MFC90. DLL), nunca de los archivos DLL de usuario. Esto se hace `CStringT` para evitar que se multiplique definido.

> [!NOTE]
> Si el código contiene la solución alternativa para los errores del vinculador que se describe en Exportación de clases de cadena [mediante CStringT](../../atl-mfc-shared/exporting-string-classes-using-cstringt.md), debe quitar ese código. Ya no es necesario.

Los siguientes tipos de cadena están disponibles en aplicaciones basadas en MFC:

|Tipo CStringT|Declaración|
|-------------------|-----------------|
|`CStringA`|Una cadena de tipo de carácter ANSI con compatibilidad con CRT.|
|`CStringW`|Una cadena de tipo de carácter Unicode con compatibilidad con CRT.|
|`CString`|Tipos de caracteres ANSI y Unicode con compatibilidad con CRT.|

Los siguientes tipos de cadena están disponibles en los proyectos en los que se define ATL_CSTRING_NO_CRT:

|Tipo CStringT|Declaración|
|-------------------|-----------------|
|`CAtlStringA`|Una cadena de tipo de carácter ANSI sin compatibilidad con CRT.|
|`CAtlStringW`|Una cadena de tipo de carácter Unicode sin compatibilidad con CRT.|
|`CAtlString`|Tipos de caracteres ANSI y Unicode sin compatibilidad con CRT.|

Los siguientes tipos de cadena están disponibles en proyectos en los que no se define ATL_CSTRING_NO_CRT:

|Tipo CStringT|Declaración|
|-------------------|-----------------|
|`CAtlStringA`|Una cadena de tipo de carácter ANSI con compatibilidad con CRT.|
|`CAtlStringW`|Una cadena de tipo de carácter Unicode con compatibilidad con CRT.|
|`CAtlString`|Tipos de caracteres ANSI y Unicode con compatibilidad con CRT.|

`CString`los objetos también tienen las siguientes características:

- `CStringT`objetos pueden crecer como resultado de las operaciones de concatenación.

- `CStringT`los objetos siguen la "semántica del valor". Piense en `CStringT` un objeto como una cadena real, no como un puntero a una cadena.

- Puede sustituir `CStringT` libremente `PCXSTR` objetos por argumentos de función.

- Administración de memoria personalizada para búferes de cadena. Para obtener más información, vea [Administración de memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="cstringt-predefined-types"></a>Tipos predefinidos CStringT

Dado `CStringT` que utiliza un argumento de plantilla para definir el tipo de carácter [(wchar_t](../../c-runtime-library/standard-types.md) o [char](../../c-runtime-library/standard-types.md)) admitido, los tipos de parámetros de método pueden ser complicados a veces. Para simplificar este problema, se define un conjunto de `CStringT` tipos predefinidos y se utiliza en toda la clase. En la tabla siguiente se enumeran los distintos tipos:

|Nombre|Descripción|
|----------|-----------------|
|`XCHAR`|Un solo carácter **(wchar_t** o **char**) `CStringT` con el mismo tipo de carácter que el objeto.|
|`YCHAR`|Un solo carácter **(wchar_t** o **char**) `CStringT` con el tipo de carácter opuesto como objeto.|
|`PXSTR`|Puntero a una cadena de **char**caracteres **(wchar_t** o char `CStringT` ) con el mismo tipo de carácter que el objeto.|
|`PYSTR`|Puntero a una cadena de **char**caracteres **(wchar_t** o char `CStringT` ) con el tipo de carácter opuesto como objeto.|
|`PCXSTR`|Puntero a una cadena de **caracteres const** **(wchar_t** o `CStringT` **char**) con el mismo tipo de carácter que el objeto.|
|`PCYSTR`|Puntero a una cadena de **caracteres const** **(wchar_t** o `CStringT` **char**) con el tipo de carácter opuesto como objeto.|

> [!NOTE]
> El código que anteriormente `CString` utilizaba `AssignCopy`métodos no documentados de (como `CStringT` ) debe `GetBuffer` `ReleaseBuffer`reemplazarse por código que utilice los siguientes métodos documentados de (como o ). Estos métodos `CSimpleStringT`se heredan de .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)

`CStringT`

## <a name="requirements"></a>Requisitos

|Encabezado|Se usa para|
|------------|-------------|
|cstringt.h|Objetos de cadena solo MFC|
|atlstr.h|Objetos de cadena que no son MFC|

## <a name="cstringtallocsysstring"></a><a name="allocsysstring"></a>CStringT::AllocSysString

Asigna una cadena compatible con Automation del tipo BSTR `CStringT` y copia el contenido del objeto en él, incluido el carácter nulo de terminación.

```
BSTR AllocSysString() const;
```

### <a name="return-value"></a>Valor devuelto

La cadena recién asignada.

### <a name="remarks"></a>Observaciones

En los programas MFC, se produce una [clase CMemoryException](../../mfc/reference/cmemoryexception-class.md) si no existe suficiente memoria. En los programas ATL, se produce una [excepción CAtlException.](../../atl/reference/catlexception-class.md) Esta función se utiliza normalmente para devolver cadenas para Automation.

Normalmente, si esta cadena se pasa a una función COM como un parámetro [in], esto requiere que el autor de la llamada libere la cadena. Esto se puede hacer mediante [SysFreeString](/windows/win32/api/oleauto/nf-oleauto-sysfreestring), como se describe en el Windows SDK. Para obtener más información, consulte [Asignación y liberación de memoria para un BSTR](../../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md).

Para obtener más información acerca de las funciones de asignación OLE en Windows, vea [SysAllocString](/windows/win32/api/oleauto/nf-oleauto-sysallocstring) en el Windows SDK.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CStringT::AllocSysString`.

[!code-cpp[NVC_ATLMFC_Utilities#105](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_1.cpp)]

## <a name="cstringtansitooem"></a><a name="ansitooem"></a>CStringT::AnsiToOem

Convierte todos los caracteres de este `CStringT` objeto del juego de caracteres ANSI en el juego de caracteres OEM.

```cpp
void AnsiToOem();
```

### <a name="remarks"></a>Observaciones

La función no está disponible si se define _UNICODE.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#106](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_2.cpp)]

## <a name="cstringtappendformat"></a><a name="appendformat"></a>CStringT::AppendFormat

Anexa datos con formato `CStringT` a un objeto existente.

```cpp
void __cdecl AppendFormat(PCXSTR pszFormat, [, argument] ...);
void __cdecl AppendFormat(UINT nFormatID, [, argument] ...);
```

### <a name="parameters"></a>Parámetros

*pszFormat*<br/>
Una cadena de control de formato.

*nFormatID*<br/>
Identificador de recurso de cadena que contiene la cadena de control de formato.

*argument*<br/>
Argumentos opcionales.

### <a name="remarks"></a>Observaciones

Esta función da formato y añade una `CStringT`serie de caracteres y valores en el archivo . Cada argumento opcional (si existe) se convierte y se anexa según la especificación de formato correspondiente en *pszFormat* o desde el recurso de cadena identificado por *nFormatID*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#107](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_3.cpp)]

## <a name="cstringtcollate"></a><a name="collate"></a>CStringT::Collate

Compara dos cadenas mediante la `_tcscoll`función de texto genérico .

```
int Collate(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parámetros

*psz*<br/>
La otra cadena utilizada para la comparación.

### <a name="return-value"></a>Valor devuelto

Cero si las cadenas son idénticas, `CStringT` < 0 si este objeto es menor que *psz*, o > 0 si este `CStringT` objeto es mayor que *psz*.

### <a name="remarks"></a>Observaciones

La función `_tcscoll`de texto genérico, que se define en TCHAR. H, se `strcoll`asigna `wcscoll`a `_mbscoll`, , o , dependiendo del juego de caracteres que se define en tiempo de compilación. Cada función realiza una comparación entre mayúsculas y minúsculas de las cadenas según la página de códigos actualmente en uso. Para obtener más información, vea [strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md).

## <a name="cstringtcollatenocase"></a><a name="collatenocase"></a>CStringT::CollateNoCase

Compara dos cadenas mediante la `_tcscoll`función de texto genérico .

```
int CollateNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parámetros

*psz*<br/>
La otra cadena utilizada para la comparación.

### <a name="return-value"></a>Valor devuelto

`CStringT` Cero si las cadenas son idénticas (ignorando mayúsculas y minúsculas), < 0 si este objeto es menor que *psz* (ignorando mayúsculas y minúsculas) o > 0 si este `CStringT` objeto es mayor que *psz* (ignorando mayúsculas y minúsculas).

### <a name="remarks"></a>Observaciones

La función `_tcscoll`de texto genérico, que se define en TCHAR. H, se `stricoll`asigna `wcsicoll`a `_mbsicoll`, , o , dependiendo del juego de caracteres que se define en tiempo de compilación. Cada función realiza una comparación entre mayúsculas y minúsculas de las cadenas, según la página de códigos actualmente en uso. Para obtener más información, vea [strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#109](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_4.cpp)]

## <a name="cstringtcompare"></a><a name="compare"></a>CStringT::Compare

Compara dos cadenas (con distinción entre mayúsculas y minúsculas).

```
int Compare(PCXSTR psz) const;
```

### <a name="parameters"></a>Parámetros

*psz*<br/>
La otra cadena utilizada para la comparación.

### <a name="return-value"></a>Valor devuelto

Cero si las cadenas son idénticas, `CStringT` < 0 si este objeto es menor que *psz*, o > 0 si este `CStringT` objeto es mayor que *psz*.

### <a name="remarks"></a>Observaciones

La función `_tcscmp`de texto genérico, que se define en TCHAR. H, se `strcmp`asigna `wcscmp`a `_mbscmp`, , o , dependiendo del juego de caracteres que se define en tiempo de compilación. Cada función realiza una comparación entre mayúsculas y minúsculas de las cadenas y no se ve afectada por la configuración regional. Para obtener más información, consulte [strcmp, wcscmp, _mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md).

Si la cadena contiene valores NULL incrustados, para fines de comparación, se considera que la cadena se trunca en el primer carácter nulo incrustado.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CStringT::Compare`.

[!code-cpp[NVC_ATLMFC_Utilities#110](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_5.cpp)]

## <a name="cstringtcomparenocase"></a><a name="comparenocase"></a>CStringT::CompareNoCase

Compara dos cadenas (sin distinción entre mayúsculas y minúsculas).

```
int CompareNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parámetros

*psz*<br/>
La otra cadena utilizada para la comparación.

### <a name="return-value"></a>Valor devuelto

`CStringT` Cero si las cadenas son idénticas (ignorando mayúsculas y minúsculas), <0 si este objeto es menor que *psz* (ignorando mayúsculas y minúsculas) o >0 si este `CStringT` objeto es mayor que *psz* (ignorando mayúsculas y minúsculas).

### <a name="remarks"></a>Observaciones

La función `_tcsicmp`de texto genérico, que se define en TCHAR. H, se `_stricmp`asigna `_wcsicmp` `_mbsicmp`a , o , dependiendo del juego de caracteres que se define en tiempo de compilación. Cada función realiza una comparación entre mayúsculas y minúsculas de las cadenas. La comparación depende del aspecto LC_CTYPE de la configuración regional, pero no de LC_COLLATE. Para obtener más información, consulte [_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#111](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_6.cpp)]

## <a name="cstringtcstringt"></a><a name="cstringt"></a>CStringT::CStringT

Construye un objeto `CStringT`.

```
CStringT() throw() :
    CThisSimpleString(StringTraits::GetDefaultManager());

explicit CStringT(IAtlStringMgr* pStringMgr) throw() :
    CThisSimpleString( pStringMgr);

CStringT(const VARIANT& varSrc);

CStringT(const VARIANT& varSrc, IAtlStringMgr* pStringMgr);

CStringT(const CStringT& strSrc) :
    CThisSimpleString( strSrc);

operator CSimpleStringT<
                    BaseType,
                    !_CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>
                    :: c_bIsMFCDLLTraits> &()

template <bool bMFCDLL>
CStringT(const CSimpleStringT<BaseType, bMFCDLL>& strSrc) :
    CThisSimpleString( strSrc);

template <class SystemString>
CStringT(SystemString^ pString) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(const XCHAR* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CSTRING_EXPLICIT CStringT(const YCHAR* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(LPCSTR pszSrc, IAtlStringMgr* pStringMgr) :
    CThisSimpleString( pStringMgr);

CStringT(LPCWSTR pszSrc, IAtlStringMgr* pStringMgr) :
    CThisSimpleString( pStringMgr);

CSTRING_EXPLICIT CStringT(const unsigned char* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

/*CSTRING_EXPLICIT*/ CStringT(char* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CSTRING_EXPLICIT CStringT(unsigned char* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CSTRING_EXPLICIT CStringT(wchar_t* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(const unsigned char* pszSrc, IAtlStringMgr* pStringMgr) :
    CThisSimpleString( pStringMgr);

CSTRING_EXPLICIT CStringT(char ch, int nLength = 1) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CSTRING_EXPLICIT CStringT(wchar_t ch, int nLength = 1) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(const XCHAR* pch, int nLength) :
    CThisSimpleString( pch, nLength, StringTraits::GetDefaultManager());

CStringT(const YCHAR* pch, int nLength) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(const XCHAR* pch, int nLength, AtlStringMgr* pStringMgr) :
    CThisSimpleString( pch, nLength, pStringMgr);

CStringT(const YCHAR* pch, int nLength, IAtlStringMgr* pStringMgr) :
    CThisSimpleString( pStringMgr);
```

### <a name="parameters"></a>Parámetros

*Pch*<br/>
Un puntero a una matriz de caracteres de longitud *nLength*, no terminada en null.

*nLongitud*<br/>
Un recuento del número de caracteres en *pch*.

*Ch*<br/>
Un solo personaje.

*pszSrc*<br/>
Cadena terminada en null que se `CStringT` va a copiar en este objeto.

*pStringMgr*<br/>
Un puntero al administrador `CStringT` de memoria para el objeto. Para obtener `IAtlStringMgr` más información `CStringT`sobre la administración de memoria y la administración de memoria para , vea Administración de [memoria con CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

*strSrc*<br/>
Objeto `CStringT` existente que se va `CStringT` a copiar en este objeto. Para obtener `CThisString` más `CThisSimpleString`información sobre y , consulte la sección Comentarios.

*varSrc*<br/>
Objeto de variante que se `CStringT` va a copiar en este objeto.

*BaseType*<br/>
El tipo de carácter de la clase de cadena. Puede ser uno de los siguientes:

**char** (para cadenas de caracteres ANSI).

**wchar_t** (para cadenas de caracteres Unicode).

TCHAR (para cadenas de caracteres ANSI y Unicode).

*bMFCDLL*<br/>
Boolean que especifica si el proyecto es un archivo DLL de MFC (TRUE) o no (FALSE).

*SystemString*<br/>
Debe `System::String`ser , y el proyecto debe compilarse con /clr.

*pString*<br/>
Un identificador `CStringT` para un objeto.

### <a name="remarks"></a>Observaciones

Dado que los constructores copian los datos de entrada en el nuevo almacenamiento asignado, debe tener en cuenta que pueden producirse excepciones de memoria. Tenga en cuenta que algunos de estos constructores actúan como funciones de conversión. Esto le permite sustituir, por ejemplo, un `CStringT` LPTSTR donde se espera un objeto.

- `CStringT`( `LPCSTR` `lpsz` ): Construye `CStringT` un Unicode a partir de una cadena ANSI. También puede usar este constructor para cargar un recurso de cadena como se muestra en el ejemplo siguiente.

- `CStringT(`): Construye `CStringT` a partir de una cadena Unicode. `LPCWSTR` `lpsz`

- `CStringT`( `const unsigned char*` `psz` ): Permite construir `CStringT` a partir de un puntero a **char sin signo**.

> [!NOTE]
> Defina la macro _CSTRING_DISABLE_NARROW_WIDE_CONVERSION para desactivar la conversión implícita de cadenas entre cadenas ANSI y Unicode. La macro se excluye de los constructores de compilación que admiten la conversión.

Tenga en cuenta que el parámetro `CStringT` *strSrc* puede ser a u `CThisSimpleString` object. Para `CStringT`, utilice una de sus`CString`instancias predeterminadas ( , `CStringA`, o `CStringW`); para `CThisSimpleString`, utilice un puntero **this.** `CThisSimpleString`declara una instancia de la [clase CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), que es una clase `CStringT` de cadena más pequeña con menos funcionalidad integrada que la clase.

El operador `CSimpleStringT<>&()` de `CStringT` sobrecarga construye `CSimpleStringT` un objeto a partir de una declaración.

> [!NOTE]
> Aunque es posible `CStringT` crear instancias que contengan caracteres nulos incrustados, se recomienda en su contra. Llamar a métodos y operadores en `CStringT` objetos que contienen caracteres nulos incrustados puede producir resultados no deseados.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#112](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_7.cpp)]

## <a name="cstringtcstringt"></a><a name="_dtorcstringt"></a>CStringT::-CStringT

Destruye el objeto `CStringT`.

```
~CStringT() throw();
```

### <a name="remarks"></a>Observaciones

Destruye el objeto `CStringT`.

## <a name="cstringtdelete"></a><a name="delete"></a>CStringT::Delete

Elimina un carácter o caracteres de una cadena que comienza con el carácter en el índice especificado.

```
int Delete(int iIndex, int nCount = 1);
```

### <a name="parameters"></a>Parámetros

*iIndex*<br/>
El índice de base cero del `CStringT` primer carácter del objeto que se va a eliminar.

*nCount*<br/>
El número de caracteres que se van a eliminar.

### <a name="return-value"></a>Valor devuelto

La longitud de la cadena modificada.

### <a name="remarks"></a>Observaciones

Si *nCount* es más largo que la cadena, se quitará el resto de la cadena.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#113](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_8.cpp)]

```Output
Before: Soccer is best,
    but hockey is quicker!
After: Soccer best,
    but hockey is quicker!
```

## <a name="cstringtfind"></a><a name="find"></a>CStringT::Buscar

Busca en esta cadena la primera coincidencia de un carácter o subcadena.

```
int Find(PCXSTR pszSub, int iStart=0) const throw();
int Find(XCHAR ch, int iStart=0) const throw();
```

### <a name="parameters"></a>Parámetros

*pszSub*<br/>
Una subcadena para buscar.

*iStart*<br/>
El índice del carácter de la cadena con el que se iniciará la búsqueda, o 0 para empezar desde el principio.

*Ch*<br/>
Un solo carácter para buscar.

### <a name="return-value"></a>Valor devuelto

El índice de base cero del `CStringT` primer carácter de este objeto que coincide con la subcadena o caracteres solicitados; -1 si no se encuentra la subcadena o el carácter.

### <a name="remarks"></a>Observaciones

La función está sobrecargada para aceptar caracteres individuales (similares a la función `strchr`en tiempo de ejecución) y cadenas (similares a `strstr`).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#114](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_9.cpp)]

## <a name="cstringtfindoneof"></a><a name="findoneof"></a>CStringT::FindoneOf

Busca en esta cadena el primer carácter que coincida con cualquier carácter contenido en *pszCharSet*.

```
int FindOneOf(PCXSTR pszCharSet) const throw();
```

### <a name="parameters"></a>Parámetros

*pszCharSet*<br/>
Cadena que contiene caracteres para la coincidencia.

### <a name="return-value"></a>Valor devuelto

El índice de base cero del primer carácter de esta cadena que también está en *pszCharSet*; -1 si no hay coincidencia.

### <a name="remarks"></a>Observaciones

Busca la primera aparición de cualquiera de los caracteres en *pszCharSet*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#115](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_10.cpp)]

## <a name="cstringtformat"></a><a name="format"></a>CStringT::Formato

Escribe datos con formato `CStringT` en un de la misma manera que [sprintf_s](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md) da formato a los datos en una matriz de caracteres de estilo C.

```cpp
void __cdecl Format(UINT nFormatID, [, argument]...);
void __cdecl Format(PCXSTR pszFormat,  [, argument] ...);
```

### <a name="parameters"></a>Parámetros

*nFormatID*<br/>
Identificador de recurso de cadena que contiene la cadena de control de formato.

*pszFormat*<br/>
Una cadena de control de formato.

*argument*<br/>
Argumentos opcionales.

### <a name="remarks"></a>Observaciones

Esta función da formato y almacena `CStringT`una serie de caracteres y valores en el archivo . Cada argumento opcional (si existe) se convierte y se genera según la especificación de formato correspondiente en *pszFormat* o desde el recurso de cadena identificado por *nFormatID*.

Se producirá un error en la llamada si `Format`el propio objeto de cadena se ofrece como parámetro a . Por ejemplo, el código siguiente producirá resultados impredecibles:

[!code-cpp[NVC_ATLMFC_Utilities#116](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_11.cpp)]

Para obtener más información, vea [Sintaxis de especificación de formato: Funciones printf y wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#117](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_12.cpp)]

## <a name="cstringtformatmessage"></a><a name="formatmessage"></a>CStringT::FormatMessage

Da formato a una cadena de mensaje.

```cpp
void __cdecl FormatMessage(UINT nFormatID, [, argument]...);
void __cdecl FormatMessage(PCXSTR pszFormat, [, argument]...);
```

### <a name="parameters"></a>Parámetros

*nFormatID*<br/>
Identificador de recurso de cadena que contiene el texto del mensaje sin formato.

*pszFormat*<br/>
Apunta a la cadena de control de formato. Se escaneará en busca de inserciones y se formateará en consecuencia. La cadena de formato es similar a las cadenas de formato *printf*-style de la función en tiempo de ejecución, excepto que permite que los parámetros se inserten en un orden arbitrario.

*argument*<br/>
Argumentos opcionales.

### <a name="remarks"></a>Observaciones

La función requiere una definición de mensaje como entrada. La definición del mensaje viene determinada por *pszFormat* o desde el recurso de cadena identificado por *nFormatID*. La función copia el texto `CStringT` del mensaje con formato en el objeto, procesando las secuencias de inserción incrustadas si se solicita.

> [!NOTE]
> `FormatMessage`intenta asignar memoria del sistema para la cadena recién formateada. Si se produce un error en este intento, se produce automáticamente una excepción de memoria.

Cada inserción debe tener un parámetro correspondiente después del parámetro *pszFormat* o *nFormatID.* Dentro del texto del mensaje, se admiten varias secuencias de escape para dar formato dinámicamente al mensaje. Para obtener más información, vea la función [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) de Windows en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#118](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_13.cpp)]

## <a name="cstringtformatmessagev"></a><a name="formatmessagev"></a>CStringT::FormatMessageV

Da formato a una cadena de mensaje mediante una lista de argumentos de variable.

```cpp
void FormatMessageV(PCXSTR pszFormat, va_list* pArgList);
```

### <a name="parameters"></a>Parámetros

*pszFormat*<br/>
Apunta a la cadena de control de formato. Se escaneará en busca de inserciones y se formateará en consecuencia. La cadena de formato es `printf`similar a las cadenas de formato de estilo de función en tiempo de ejecución, excepto que permite que los parámetros se inserten en un orden arbitrario.

*pArgList*<br/>
Puntero a una lista de argumentos.

### <a name="remarks"></a>Observaciones

La función requiere una definición de mensaje como entrada, determinada por *pszFormat*. La función copia el texto del mensaje con `CStringT` formato y una lista variable de argumentos en el objeto, procesando las secuencias de inserción incrustadas si se solicitan.

> [!NOTE]
> `FormatMessageV`llama a [CStringT::FormatMessage](#formatmessage), que intenta asignar memoria del sistema para la cadena recién formateada. Si se produce un error en este intento, se produce automáticamente una excepción de memoria.

Para obtener más información, vea la función [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) de Windows en el Windows SDK.

## <a name="cstringtformatv"></a><a name="formatv"></a>CStringT::FormatV

Da formato a una cadena de mensaje mediante una lista de argumentos de variable.

```cpp
void FormatV(PCXSTR pszFormat, va_list args);
```

### <a name="parameters"></a>Parámetros

*pszFormat*<br/>
Apunta a la cadena de control de formato. Se escaneará en busca de inserciones y se formateará en consecuencia. La cadena de formato es `printf`similar a las cadenas de formato de estilo de función en tiempo de ejecución, excepto que permite que los parámetros se inserten en un orden arbitrario.

*args*<br/>
Puntero a una lista de argumentos.

### <a name="remarks"></a>Observaciones

Escribe una cadena con formato y una lista `CStringT` de variables `vsprintf_s` de argumentos en una cadena de la misma manera que da formato a los datos en una matriz de caracteres de estilo C.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#119](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_14.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#120](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_15.cpp)]

## <a name="cstringtgetenvironmentvariable"></a><a name="getenvironmentvariable"></a>CStringT::GetEnvironmentVariable

Establece la cadena en el valor de la variable de entorno especificada.

```
BOOL GetEnvironmentVariable(PCXSTR pszVar);
```

### <a name="parameters"></a>Parámetros

*pszVar*<br/>
Puntero a una cadena terminada en null que especifica la variable de entorno.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Recupera el valor de la variable especificada del bloque de entorno del proceso de llamada. El valor tiene la forma de una cadena de caracteres terminada en null.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#121](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_16.cpp)]

## <a name="cstringtinsert"></a><a name="insert"></a>CStringT::Insertar

Inserta un solo carácter o una subcadena en el índice especificado dentro de la cadena.

```
int Insert(int iIndex, PCXSTR psz);
int Insert(int iIndex, XCHAR ch);
```

### <a name="parameters"></a>Parámetros

*iIndex*<br/>
El índice del carácter antes del cual se llevará a cabo la inserción.

*psz*<br/>
Puntero a la subcadena que se va a insertar.

*Ch*<br/>
El carácter que se va a insertar.

### <a name="return-value"></a>Valor devuelto

La longitud de la cadena modificada.

### <a name="remarks"></a>Observaciones

El parámetro *iIndex* identifica el primer carácter que se moverá para dejar espacio para el carácter o subcadena. Si *nIndex* es cero, la inserción se producirá antes de toda la cadena. Si *nIndex* es mayor que la longitud de la cadena, la función concatenará la cadena actual y el nuevo material proporcionado por *ch* o *psz*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#122](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_17.cpp)]

## <a name="cstringtleft"></a><a name="left"></a>CStringT::Izquierda

Extrae los caracteres *nCount* más a la izquierda de este `CStringT` objeto y devuelve una copia de la subcadena extraída.

```
CStringT Left(int nCount) const;
```

### <a name="parameters"></a>Parámetros

*nCount*<br/>
Número de caracteres que se va a extraer de este objeto `CStringT`.

### <a name="return-value"></a>Valor devuelto

El objeto `CStringT` que contiene una copia del rango de caracteres especificado. El objeto `CStringT` devuelto puede estar vacío.

### <a name="remarks"></a>Observaciones

Si *nCount* supera la longitud de la cadena, se extrae toda la cadena. `Left` es similar a la función `Left` de Basic.

Para los conjuntos de caracteres multibyte (MBCS), *nCount* trata cada secuencia de 8 bits como un carácter, de modo que *nCount* devuelve el número de caracteres multibyte multiplicado por dos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#123](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_18.cpp)]

## <a name="cstringtloadstring"></a><a name="loadstring"></a>CStringT::LoadString

Lee un recurso de cadena de Windows, `CStringT` identificado por *nID*, en un objeto existente.

```
BOOL LoadString(HINSTANCE hInstance, UINT nID, WORD wLanguageID);
BOOL LoadString(HINSTANCE hInstance, UINT nID);
BOOL LoadString(UINT nID);
```

### <a name="parameters"></a>Parámetros

*hInstance*<br/>
Un identificador de la instancia del módulo.

*nID*<br/>
Un identificador de recurso de cadena de Windows.

*wLanguageID*<br/>
El idioma del recurso de cadena.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la carga de recursos se realizó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Carga el recurso de cadena (*nID*) desde el módulo especificado (*hInstance*) utilizando el idioma especificado (*wLanguage*).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#124](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_19.cpp)]

## <a name="cstringtmakelower"></a><a name="makelower"></a>CStringT::MakeLower

Convierte el `CStringT` objeto en una cadena en minúsculas.

```
CStringT& MakeLower();
```

### <a name="return-value"></a>Valor devuelto

La cadena en minúsculas resultante.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#125](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_20.cpp)]

## <a name="cstringtmakereverse"></a><a name="makereverse"></a>CStringT::MakeReverse

Invierte el orden de los `CStringT` caracteres del objeto.

```
CStringT& MakeReverse();
```

### <a name="return-value"></a>Valor devuelto

La cadena invertida resultante.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#126](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_21.cpp)]

## <a name="cstringtmakeupper"></a><a name="makeupper"></a>CStringT::MakeUpper

Convierte el `CStringT` objeto en una cadena en mayúsculas.

```
CStringT& MakeUpper();
```

### <a name="return-value"></a>Valor devuelto

La cadena en mayúsculas resultante.

### <a name="remarks"></a>Observaciones

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#127](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_22.cpp)]

## <a name="cstringtmid"></a><a name="mid"></a>CStringT::Mid

Extrae una subcadena de caracteres `CStringT` *nCount* de longitud de este objeto, comenzando en la posición *iFirst* (basada en cero).

```
CStringT Mid(int iFirst, int nCount) const;
CStringT Mid(int iFirst) const;
```

### <a name="parameters"></a>Parámetros

*iFirst*<br/>
El índice de base cero del `CStringT` primer carácter de este objeto que se va a incluir en la subcadena extraída.

*nCount*<br/>
Número de caracteres que se va a extraer de este objeto `CStringT`. Si no se proporciona este parámetro, se extrae el resto de la cadena.

### <a name="return-value"></a>Valor devuelto

El objeto `CStringT` que contiene una copia del rango de caracteres especificado. Tenga en `CStringT` cuenta que el objeto devuelto puede estar vacío.

### <a name="remarks"></a>Observaciones

La función devuelve una copia de la subcadena extraída. `Mid`es similar a la función Media básica (excepto que los índices de Basic se basan en uno).

Para conjuntos de caracteres multibyte (MBCS), *nCount* hace referencia a cada carácter de 8 bits; es decir, un byte de cliente potencial y de seguimiento en un carácter multibyte se cuentan como dos caracteres.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#128](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_23.cpp)]

## <a name="cstringtoemtoansi"></a><a name="oemtoansi"></a>CStringT::OemToAnsi

Convierte todos los caracteres de este `CStringT` objeto del juego de caracteres OEM en el juego de caracteres ANSI.

```cpp
void OemToAnsi();
```

### <a name="remarks"></a>Observaciones

Esta función no está disponible si se define _UNICODE.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CStringT::AnsiToOem](#ansitooem).

## <a name="cstringtoperator-"></a><a name="operator_eq"></a>CStringT::operador ?

Asigna un nuevo valor a la cadena.

```
CStringT& operator=(const CStringT& strSrc);

template<bool bMFCDLL>
CStringT& operator=(const CSimpleStringT<BaseType, bMFCDLL>& str);

CStringT& operator=(PCXSTR pszSrc);
CStringT& operator=(PCYSTR pszSrc);
CStringT& operator=(const unsigned char* pszSrc);
CStringT& operator=(XCHAR ch);
CStringT& operator=(YCHAR ch);
CStringT& operator=(const VARIANT& var);
```

### <a name="parameters"></a>Parámetros

*strSrc*<br/>
A `CStringT` para asignar a esta cadena.

*Str*<br/>
Referencia a un objeto `CThisSimpleString`.

*bMFCDLL*<br/>
Un booleano que especifica si el proyecto es un archivo DLL de MFC o no.

*BaseType*<br/>
El tipo base de cadena.

*var*<br/>
Objeto de variante que se va a asignar a esta cadena.

*Ch*<br/>
Un carácter ANSI o Unicode para asignar a la cadena.

*pszSrc*<br/>
Un puntero a la cadena original que se va a asignar.

### <a name="remarks"></a>Observaciones

El operador de `CStringT` asignación acepta otro objeto, un puntero de carácter o un solo carácter. Debe tener en cuenta que pueden producirse excepciones de memoria siempre que utilice este operador porque se puede asignar nuevo almacenamiento.

Para obtener `CThisSimpleString`información sobre , vea la sección Comentarios de [CStringT::CStringT](#cstringt).

> [!NOTE]
> Aunque es posible `CStringT` crear instancias que contengan caracteres nulos incrustados, se recomienda en su contra. Llamar a métodos y operadores en `CStringT` objetos que contienen caracteres nulos incrustados puede producir resultados no deseados.

## <a name="cstringtoperator-"></a><a name="operator_add"></a>CStringT::operador +

Concatena dos cadenas o un carácter y una cadena.

```
friend CStringT operator+(const CStringT& str1, const CStringT& str2);
friend CStringT operator+(const CStringT& str1, PCXSTR psz2);
friend CStringT operator+(PCXSTR psz1, const CStringT& str2,);
friend CStringT operator+(char ch1, const CStringT& str2,);
friend CStringT operator+(const CStringT& str1, char ch2);
friend CStringT operator+(const CStringT& str1, wchar_t ch2);
friend CStringT operator+(wchar_t ch1, const CStringT& str2,);
```

### <a name="parameters"></a>Parámetros

*ch1*<br/>
Un carácter ANSI o Unicode para concatenar con una cadena.

*ch2*<br/>
Un carácter ANSI o Unicode para concatenar con una cadena.

*str1*<br/>
A `CStringT` concatenar con una cadena o un carácter.

*str2*<br/>
A `CStringT` concatenar con una cadena o un carácter.

*psz1*<br/>
Puntero a una cadena terminada en null para concatenar con una cadena o carácter.

*psz2*<br/>
Puntero a una cadena para concatenar con una cadena o un carácter.

### <a name="remarks"></a>Observaciones

Hay siete formas de `CStringT::operator+` sobrecarga de la función. La primera versión concatena `CStringT` dos objetos existentes. Los dos siguientes `CStringT` concatenan un objeto y una cadena terminada en null. Los dos siguientes `CStringT` concatenan un objeto y un carácter ANSI. Los dos últimos `CStringT` concatenan un objeto y un carácter Unicode.

> [!NOTE]
> Aunque es posible `CStringT` crear instancias que contengan caracteres nulos incrustados, se recomienda en su contra. Llamar a métodos y operadores en `CStringT` objetos que contienen caracteres nulos incrustados puede producir resultados no deseados.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#140](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_24.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_add_eq"></a>CStringT::operador +o

Concatena los caracteres al final de la cadena.

```
CStringT& operator+=(const CThisSimpleString& str);

template<bool bMFCDLL>
CStringT& operator+=(const const CSimpleStringT<BaseType, bMFCDLL>& str);

template<int t_nSize>
CStringT& operator+=(const CStaticString<XCHAR, t_nSize>& strSrc);
CStringT& operator+=(PCXSTR pszSrc);
CStringT& operator+=(PCYSTR pszSrc);
CStringT& operator+=(char ch);
CStringT& operator+=(unsigned char ch);
CStringT& operator+=(wchar_t ch);
CStringT& operator+=(const VARIANT& var);
```

### <a name="parameters"></a>Parámetros

*Str*<br/>
Referencia a un objeto `CThisSimpleString`.

*bMFCDLL*<br/>
Un booleano que especifica si el proyecto es un archivo DLL de MFC o no.

*BaseType*<br/>
El tipo base de cadena.

*var*<br/>
Objeto de variante que se va a concatenar a esta cadena.

*Ch*<br/>
Un carácter ANSI o Unicode para concatenar con una cadena.

*pszSrc*<br/>
Puntero a la cadena original que se está concatenando.

*strSrc*<br/>
A `CStringT` concatenar a esta cadena.

### <a name="remarks"></a>Observaciones

El operador acepta `CStringT` otro objeto, un puntero de carácter o un solo carácter. Debe tener en cuenta que pueden producirse excepciones de memoria siempre que utilice `CStringT` este operador de concatenación porque se puede asignar nuevo almacenamiento para los caracteres agregados a este objeto.

Para obtener `CThisSimpleString`información sobre , vea la sección Comentarios de [CStringT::CStringT](#cstringt).

> [!NOTE]
> Aunque es posible `CStringT` crear instancias que contengan caracteres nulos incrustados, se recomienda en su contra. Llamar a métodos y operadores en `CStringT` objetos que contienen caracteres nulos incrustados puede producir resultados no deseados.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#141](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_25.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_eq_eq"></a>CStringT::operador ?

Determina si dos cadenas son lógicamente iguales.

```
friend bool operator==(const CStringT& str1, const CStringT& str2) throw();
friend bool operator==(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator==(const CStringT& str1, PCYSTR psz2) throw();
friend bool operator==(const CStringT& str1, XCHAR ch2) throw();
friend bool operator==(PCXSTR psz1, const CStringT& str2) throw();
friend bool operator==(PCYSTR psz1, const CStringT& str2,) throw();
friend bool operator==(XCHAR ch1, const CStringT& str2,) throw();
```

### <a name="parameters"></a>Parámetros

*ch1*<br/>
Un carácter ANSI o Unicode para la comparación.

*ch2*<br/>
Un carácter ANSI o Unicode para la comparación.

*str1*<br/>
A `CStringT` para la comparación.

*str2*<br/>
A `CStringT` para la comparación.

*psz1*<br/>
Un puntero a una cadena terminada en null para la comparación.

*psz2*<br/>
Un puntero a una cadena terminada en null para la comparación.

### <a name="remarks"></a>Observaciones

Comprueba si una cadena o un carácter en el lado izquierdo es igual a una cadena o carácter en el lado derecho y devuelve TRUE o FALSE en consecuencia.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#142](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_26.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_neq"></a>CStringT::operador !-

Determina si dos cadenas lógicamente no son iguales.

```
friend bool operator!=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator!=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator!=(const CStringT& str1, PCYSTR psz2) throw();
friend bool operator!=(const CStringT& str1, XCHAR ch2) throw();
friend bool operator!=(PCXSTR psz1, const CStringT& str2) throw();
friend bool operator!=(PCYSTR psz1, const CStringT& str2,) throw();
friend bool operator!=(XCHAR ch1, const CStringT& str2,) throw();
```

### <a name="parameters"></a>Parámetros

*ch1*<br/>
Un carácter ANSI o Unicode para concatenar con una cadena.

*ch2*<br/>
Un carácter ANSI o Unicode para concatenar con una cadena.

*str1*<br/>
A `CStringT` para la comparación.

*str2*<br/>
A `CStringT` para la comparación.

*psz1*<br/>
Un puntero a una cadena terminada en null para la comparación.

*psz2*<br/>
Un puntero a una cadena terminada en null para la comparación.

### <a name="remarks"></a>Observaciones

Comprueba si una cadena o carácter en el lado izquierdo no es igual a una cadena o carácter en el lado derecho.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#143](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_27.cpp)]

## <a name="cstringtoperator-lt"></a><a name="operator_lt"></a>CStringT::operator&lt;

Determina si la cadena en el lado izquierdo del operador es menor que la cadena en el lado derecho.

```
friend bool operator<(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parámetros

*str1*<br/>
A `CStringT` para la comparación.

*str2*<br/>
A `CStringT` para la comparación.

*psz1*<br/>
Un puntero a una cadena terminada en null para la comparación.

*psz2*<br/>
Un puntero a una cadena terminada en null para la comparación.

### <a name="remarks"></a>Observaciones

Una comparación lexicográfica entre cadenas, carácter por carácter hasta:

- Encuentra dos caracteres correspondientes distintos y el resultado de la comparación se toma como el resultado de la comparación entre las cadenas.

- No encuentra ninguna desigualdad, pero una cadena tiene más caracteres que la otra y la cadena más corta se considera menor que la cadena más larga.

- No encuentra ninguna desigualdad y encuentra que las cadenas tienen el mismo número de caracteres, por lo que las cadenas son iguales.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#144](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_28.cpp)]

## <a name="cstringtoperator-gt"></a><a name="operator_gt"></a>CStringT::operator&gt;

Determina si la cadena en el lado izquierdo del operador es mayor que la cadena en el lado derecho.

```
friend bool operator>(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parámetros

*str1*<br/>
A `CStringT` para la comparación.

*str2*<br/>
A `CStringT` para la comparación.

*psz1*<br/>
Un puntero a una cadena terminada en null para la comparación.

*psz2*<br/>
Un puntero a una cadena terminada en null para la comparación.

### <a name="remarks"></a>Observaciones

Una comparación lexicográfica entre cadenas, carácter por carácter hasta:

- Encuentra dos caracteres correspondientes distintos y el resultado de la comparación se toma como el resultado de la comparación entre las cadenas.

- No encuentra ninguna desigualdad, pero una cadena tiene más caracteres que la otra y la cadena más corta se considera menor que la cadena más larga.

- No encuentra ninguna desigualdad y encuentra que las cadenas tienen el mismo número de caracteres, por lo que las cadenas son iguales.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#145](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_29.cpp)]

## <a name="cstringtoperator-lt"></a><a name="operator_lt_eq"></a>CStringT::operator&lt;=

Determina si la cadena en el lado izquierdo del operador es menor o igual que la cadena en el lado derecho.

```
friend bool operator<=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parámetros

*str1*<br/>
A `CStringT` para la comparación.

*str2*<br/>
A `CStringT` para la comparación.

*psz1*<br/>
Un puntero a una cadena terminada en null para la comparación.

*psz2*<br/>
Un puntero a una cadena terminada en null para la comparación.

### <a name="remarks"></a>Observaciones

Una comparación lexicográfica entre cadenas, carácter por carácter hasta:

- Encuentra dos caracteres correspondientes distintos y el resultado de la comparación se toma como el resultado de la comparación entre las cadenas.

- No encuentra ninguna desigualdad, pero una cadena tiene más caracteres que la otra y la cadena más corta se considera menor que la cadena más larga.

- No encuentra ninguna desigualdad y encuentra que las cadenas tienen el mismo número de caracteres, por lo que las cadenas son iguales.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#146](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_30.cpp)]

## <a name="cstringtoperator-gt"></a><a name="operator_gt_eq"></a>CStringT::operator&gt;=

Determina si la cadena en el lado izquierdo del operador es mayor o igual que la cadena en el lado derecho.

```
friend bool operator>=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parámetros

*str1*<br/>
A `CStringT` para la comparación.

*str2*<br/>
A `CStringT` para la comparación.

*psz1*<br/>
Un puntero a una cadena para la comparación.

*psz2*<br/>
Un puntero a una cadena para la comparación.

### <a name="remarks"></a>Observaciones

Una comparación lexicográfica entre cadenas, carácter por carácter hasta:

- Encuentra dos caracteres correspondientes distintos y el resultado de la comparación se toma como el resultado de la comparación entre las cadenas.

- No encuentra ninguna desigualdad, pero una cadena tiene más caracteres que la otra y la cadena más corta se considera menor que la cadena más larga.

- No encuentra ninguna desigualdad y encuentra que las cadenas tienen el mismo número de caracteres, por lo que las cadenas son iguales.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#147](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_31.cpp)]

## <a name="cstringtremove"></a><a name="remove"></a>CStringT::Quitar

Quita todas las instancias del carácter especificado de la cadena.

```
int Remove(XCHAR chRemove);
```

### <a name="parameters"></a>Parámetros

*chRemove*<br/>
El carácter que se va a quitar de una cadena.

### <a name="return-value"></a>Valor devuelto

El recuento de caracteres eliminados de la cadena. Cero si no se cambia la cadena.

### <a name="remarks"></a>Observaciones

Las comparaciones para el carácter distinguen entre mayúsculas y minúsculas.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#129](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_32.cpp)]

## <a name="cstringtreplace"></a><a name="replace"></a>CStringT::Reemplazar

Hay dos versiones de `Replace`. La primera versión reemplaza una o varias copias de una subcadena mediante otra subcadena. Ambas subcadenas terminan en null. La segunda versión reemplaza una o más copias de un carácter mediante otro carácter. Ambas versiones funcionan en `CStringT`los datos de caracteres almacenados en .

```
int Replace(PCXSTR pszOld, PCXSTR pszNew);
int Replace(XCHAR chOld, XCHAR chNew);
```

### <a name="parameters"></a>Parámetros

*pszOld*<br/>
Puntero a una cadena terminada en null que se reemplazará por *pszNew*.

*pszNew*<br/>
Puntero a una cadena terminada en null que reemplaza *pszOld*.

*chOld*<br/>
El carácter que se reemplazará por *chNew*.

*chNew*<br/>
El carácter que reemplaza *chOld*.

### <a name="return-value"></a>Valor devuelto

Devuelve el número de instancias reemplazadas del carácter o subcadena, o cero si no se cambia la cadena.

### <a name="remarks"></a>Observaciones

`Replace`puede cambiar la longitud de la cadena porque *pszNew* y *pszOld* no tienen que tener la misma longitud, y varias copias de la subcadena antigua se pueden cambiar a la nueva. La función realiza una coincidencia que distingue mayúsculas de minúsculas.

Ejemplos `CStringT` de instancias `CStringA`son `CStringW` `CString`, , y .

Para `CStringA` `Replace` , funciona con caracteres ANSI o multibyte (MBCS). Para `CStringW` `Replace` , funciona con caracteres anchos.

Para `CString`, el tipo de datos de carácter se selecciona en tiempo de compilación, en función de si se definen las constantes de la tabla siguiente.

|Constante definida|Tipo de datos de caracteres|
|----------------------|-------------------------|
|_UNICODE|Caracteres anchos|
|_MBCS|Caracteres multibyte|
|Neither|Caracteres de un solo byte|
|Ambos|No definido|

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#200](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_33.cpp)]

## <a name="cstringtreversefind"></a><a name="reversefind"></a>CStringT::ReverseFind

Busca en `CStringT` este objeto la última coincidencia de un carácter.

```
int ReverseFind(XCHAR ch) const throw();
```

### <a name="parameters"></a>Parámetros

*Ch*<br/>
El personaje que hay que buscar.

### <a name="return-value"></a>Valor devuelto

El índice de base cero del `CStringT` último carácter de este objeto que coincide con el carácter solicitado, o -1 si no se encuentra el carácter.

### <a name="remarks"></a>Observaciones

La función es similar a `strrchr`la función de tiempo de ejecución.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#130](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_34.cpp)]

## <a name="cstringtright"></a><a name="right"></a>CStringT::Right

Extrae los últimos (es decir, más `CStringT` a la derecha) *nCount* caracteres de este objeto y devuelve una copia de la subcadena extraída.

```
CStringT Right(int nCount) const;
```

### <a name="parameters"></a>Parámetros

*nCount*<br/>
Número de caracteres que se va a extraer de este objeto `CStringT`.

### <a name="return-value"></a>Valor devuelto

El objeto `CStringT` que contiene una copia del rango de caracteres especificado. Tenga en `CStringT` cuenta que el objeto devuelto puede estar vacío.

### <a name="remarks"></a>Observaciones

Si *nCount* supera la longitud de la cadena, se extrae toda la cadena. `Right`es similar a `Right` la función Basic (excepto que los índices de Basic están basados en cero).

Para conjuntos de caracteres multibyte (MBCS), *nCount* hace referencia a cada carácter de 8 bits; es decir, un byte de cliente potencial y de seguimiento en un carácter multibyte se cuentan como dos caracteres.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#131](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_35.cpp)]

## <a name="cstringtsetsysstring"></a><a name="setsysstring"></a>CStringT::SetSysString

Reasigna el BSTR al que apunta *pbstr* `CStringT` y copia el contenido del objeto en él, incluido el carácter NULL.

```
BSTR SetSysString(BSTR* pbstr) const;
```

### <a name="parameters"></a>Parámetros

*pbstr*<br/>
Un puntero a una cadena de caracteres.

### <a name="return-value"></a>Valor devuelto

La nueva cadena.

### <a name="remarks"></a>Observaciones

Dependiendo del contenido `CStringT` del objeto, el valor del BSTR al que hace referencia *pbstr* puede cambiar. La función `CMemoryException` produce una memoria si no existe suficiente.

Esta función se utiliza normalmente para cambiar el valor de las cadenas pasadas por referencia para Automation.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#132](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_36.cpp)]

## <a name="cstringtspanexcluding"></a><a name="spanexcluding"></a>CStringT::SpanExcluding

Extrae caracteres de la cadena, empezando por el primer carácter, que no están en el conjunto de caracteres identificados por *pszCharSet*.

```
CStringT SpanExcluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>Parámetros

*pszCharSet*<br/>
Cadena interpretada como un conjunto de caracteres.

### <a name="return-value"></a>Valor devuelto

Subcadena que contiene caracteres en la cadena que no están en *pszCharSet*, comenzando por el primer carácter de la cadena y terminando con el primer carácter encontrado en la cadena que también está en *pszCharSet* (es decir, empezando por el primer carácter de la cadena y hasta pero excluyendo el primer carácter de la cadena que se encuentra *pszCharSet*). Devuelve toda la cadena si no se encuentra ningún carácter en *pszCharSet* en la cadena.

### <a name="remarks"></a>Observaciones

`SpanExcluding`extrae y devuelve todos los caracteres que preceden a la primera aparición de un carácter de *pszCharSet* (en otras palabras, el carácter de *pszCharSet* y todos los caracteres que lo siguen en la cadena, no se devuelven). Si no se encuentra ningún carácter de `SpanExcluding` *pszCharSet* en la cadena, devuelve toda la cadena.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#133](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_37.cpp)]

## <a name="cstringtspanincluding"></a><a name="spanincluding"></a>CStringT::SpanIncluding

Extrae caracteres de la cadena, empezando por el primer carácter, que se encuentran en el conjunto de caracteres identificados por *pszCharSet*.

```
CStringT SpanIncluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>Parámetros

*pszCharSet*<br/>
Cadena interpretada como un conjunto de caracteres.

### <a name="return-value"></a>Valor devuelto

Subcadena que contiene caracteres en la cadena que están en *pszCharSet*, comenzando por el primer carácter de la cadena y terminando cuando se encuentra un carácter en la cadena que no está en *pszCharSet*. `SpanIncluding`devuelve una subcadena vacía si el primer carácter de la cadena no está en el conjunto especificado.

### <a name="remarks"></a>Observaciones

Si el primer carácter de la cadena `SpanIncluding` no está en el juego de caracteres, devuelve una cadena vacía. De lo contrario, devuelve una secuencia de caracteres consecutivos que se encuentran en el conjunto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#134](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_38.cpp)]

## <a name="cstringttokenize"></a><a name="tokenize"></a>CStringT::Tokenize

Busca el siguiente token en una cadena de destino

```
CStringT Tokenize(PCXSTR pszTokens, int& iStart) const;
```

### <a name="parameters"></a>Parámetros

*pszTokens*<br/>
Cadena que contiene delimitadores de token. El orden de estos delimitadores no es importante.

*iStart*<br/>
El índice de base cero para iniciar la búsqueda.

### <a name="return-value"></a>Valor devuelto

Objeto `CStringT` que contiene el valor del token actual.

### <a name="remarks"></a>Observaciones

La `Tokenize` función busca el siguiente token en la cadena de destino. El conjunto de caracteres de *pszTokens* especifica los posibles delimitadores del token que se va a encontrar. En cada `Tokenize` llamada a la función comienza en *iStart*, `CStringT` omite los delimitadores iniciales y devuelve un objeto que contiene el token actual, que es la cadena de caracteres hasta el siguiente carácter delimitador. El valor de *iStart* se actualiza para que sea la posición que sigue al carácter delimitador final, o -1 si se alcanzó el final de la cadena. Se pueden desglosar más tokens del resto de la `Tokenize`cadena de destino mediante una serie de llamadas a , mediante *iStart* para realizar un seguimiento de dónde se va a leer el siguiente token en la cadena. Cuando no haya más tokens, la función devolverá una cadena vacía y *iStart* se establecerá en -1.

A diferencia de las funciones de tokenize de CRT `Tokenize` como [strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l](../../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md), no modifica la cadena de destino.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#135](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_39.cpp)]

### <a name="remarks"></a>Observaciones

La salida de este ejemplo es la siguiente:

```Output
Resulting Token: First
Resulting Token: Second
Resulting Token: Third
```

## <a name="cstringttrim"></a><a name="trim"></a>CStringT::Trim

Recorta los caracteres iniciales y finales de la cadena.

```
CStringT& Trim(XCHAR chTarget);
CStringT& Trim(PCXSTR pszTargets);
CStringT& Trim();
```

### <a name="parameters"></a>Parámetros

*chTarget*<br/>
El carácter de destino que se va a recortar.

*pszTargets*<br/>
Puntero a una cadena que contiene los caracteres de destino que se van a recortar. Todas las apariciones iniciales y finales de caracteres `CStringT` en *pszTarget* se recortarán del objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve la cadena recortada.

### <a name="remarks"></a>Observaciones

Elimina todas las apariciones iniciales y finales de una de las siguientes:

- Carácter especificado por *chTarget*.

- Todos los caracteres encontrados en la cadena especificada por *pszTargets*.

- Espacios.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#136](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_40.cpp)]

### <a name="remarks"></a>Observaciones

La salida de este ejemplo es la siguiente:

```Output
Before: "******Soccer is best, but liquor is quicker!!!!!"
After : "Soccer is best, but liquor is quicker"
```

## <a name="cstringttrimleft"></a><a name="trimleft"></a>CStringT::TrimLeft

Recorta los caracteres iniciales de la cadena.

```
CStringT& TrimLeft(XCHAR chTarget);
CStringT& TrimLeft(PCXSTR pszTargets);
CStringT& TrimLeft();
```

### <a name="parameters"></a>Parámetros

*chTarget*<br/>
El carácter de destino que se va a recortar.

*pszTargets*<br/>
Puntero a una cadena que contiene los caracteres de destino que se van a recortar. Todas las apariciones iniciales de caracteres en `CStringT` *pszTarget* se recortarán del objeto.

### <a name="return-value"></a>Valor devuelto

La cadena recortada resultante.

### <a name="remarks"></a>Observaciones

Elimina todas las apariciones iniciales y finales de una de las siguientes:

- Carácter especificado por *chTarget*.

- Todos los caracteres encontrados en la cadena especificada por *pszTargets*.

- Espacios.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#137](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_41.cpp)]

## <a name="cstringttrimright"></a><a name="trimright"></a>CStringt::TrimRight

Recorta los caracteres finales de la cadena.

```
CStringT& TrimRight(XCHAR chTarget);
CStringT& TrimRight(PCXSTR pszTargets);
CStringT& TrimRight();
```

### <a name="parameters"></a>Parámetros

*chTarget*<br/>
El carácter de destino que se va a recortar.

*pszTargets*<br/>
Puntero a una cadena que contiene los caracteres de destino que se van a recortar. Todas las repeticiones finales de caracteres en `CStringT` *pszTarget* se recortarán del objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve `CStringT` el objeto que contiene la cadena recortada.

### <a name="remarks"></a>Observaciones

Elimina las repeticiones finales de una de las siguientes opciones:

- Carácter especificado por *chTarget*.

- Todos los caracteres encontrados en la cadena especificada por *pszTargets*.

- Espacios.

La `CStringT& TrimRight(XCHAR chTarget)` versión acepta un parámetro de carácter y quita `CStringT` todas las copias de ese carácter del final de los datos de cadena. Comienza desde el final de la cuerda y funciona hacia el frente. Se detiene cuando encuentra un `CSTringT` carácter diferente o cuando se queda sin datos de caracteres.

La `CStringT& TrimRight(PCXSTR pszTargets)` versión acepta una cadena terminada en null que contiene todos los caracteres diferentes para buscar. Elimina todas las copias de `CStringT` esos caracteres en el objeto. Comienza al final de la cuerda y funciona hacia el frente. Se detiene cuando encuentra un carácter que no `CStringT` está en la cadena de destino o cuando se queda sin datos de caracteres. No intenta hacer coincidir toda la cadena de destino `CStringT`con una subcadena al final de .

La `CStringT& TrimRight()` versión no requiere parámetros. Recorta los caracteres de espacio en `CStringT` blanco finales desde el final de la cadena. Los caracteres de espacio en blanco pueden ser saltos de línea, espacios o tabulaciones.

-

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#138](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_42.cpp)]

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases compartidas ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)<br/>
[Clase CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)
