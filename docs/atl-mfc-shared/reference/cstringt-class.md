---
title: CStringT (clase)
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
ms.openlocfilehash: a411ed54a73a0dee49ebbd9ccacbd7c6f8e69ca5
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423565"
---
# <a name="cstringt-class"></a>CStringT (clase)

Esta clase representa un objeto de `CStringT`.

## <a name="syntax"></a>Sintaxis

```
template<typename BaseType, class StringTraits>
class CStringT :
    public CSimpleStringT<BaseType,
        _CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>::c_bIsMFCDLLTraits>
```

#### <a name="parameters"></a>Parámetros

*BaseType*<br/>
Tipo de carácter de la clase String. Puede ser uno de los siguientes:

- **Char** (para cadenas de caracteres ANSI).

- **wchar_t** (para cadenas de caracteres Unicode).

- TCHAR (para cadenas de caracteres ANSI y Unicode).

*StringTraits*<br/>
Determina si la clase de cadena necesita compatibilidad con la biblioteca en tiempo de ejecución de C (CRT) y dónde se encuentran los recursos de cadena. Puede ser uno de los siguientes:

- **StrTraitATL < wchar_t** &#124; **Char** &#124; **TCHAR, ChTraitsCRT < wchar_t** &#124; **Char** &#124; **TCHAR > >**

   La clase requiere compatibilidad con CRT y busca cadenas de recursos en el módulo especificado por `m_hInstResource` (un miembro de la clase de módulo de la aplicación).

- **StrTraitATL < wchar_t** &#124; **Char** &#124; **TCHAR, ChTraitsOS < wchar_t** &#124; **Char** &#124; **TCHAR > >**

   La clase no requiere compatibilidad con CRT y busca cadenas de recursos en el módulo especificado por `m_hInstResource` (un miembro de la clase de módulo de la aplicación).

- **StrTraitMFC < wchar_t** &#124; **Char** &#124; **TCHAR, ChTraitsCRT < wchar_t** &#124; **Char** &#124; **TCHAR > >**

   La clase requiere compatibilidad con CRT y busca cadenas de recursos mediante el algoritmo de búsqueda de MFC estándar.

- **StrTraitMFC < wchar_t** &#124; **Char** &#124; **TCHAR, ChTraitsOS < wchar_t** &#124; **Char** &#124; **TCHAR > >**

   La clase no requiere compatibilidad con CRT y busca cadenas de recursos mediante el algoritmo de búsqueda de MFC estándar.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CStringT:: CStringT](#cstringt)|Construye un objeto `CStringT` de varias maneras.|
|[CStringT:: ~ CStringT](#_dtorcstringt)|Destruye un objeto `CStringT`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CStringT:: AllocSysString](#allocsysstring)|Asigna un BSTR a partir de `CStringT` datos.|
|[CStringT:: AnsiToOem](#ansitooem)|Realiza una conversión en contexto del juego de caracteres ANSI al Juego de caracteres OEM.|
|[CStringT:: AppendFormat](#appendformat)|Anexa datos con formato a un objeto de `CStringT` existente.|
|[CStringT:: COLLATE](#collate)|Compara dos cadenas (distingue mayúsculas de minúsculas, usa información específica de la configuración regional).|
|[CStringT:: CollateNoCase](#collatenocase)|Compara dos cadenas (no distingue mayúsculas de minúsculas, usa información específica de la configuración regional).|
|[CStringT:: Compare](#compare)|Compara dos cadenas (distingue mayúsculas de minúsculas).|
|[CStringT:: CompareNoCase](#comparenocase)|Compara dos cadenas (no distingue mayúsculas de minúsculas).|
|[CStringT::D iminar](#delete)|Elimina un carácter o caracteres de una cadena.|
|[CStringT:: Find](#find)|Busca un carácter o subcadena dentro de una cadena más grande.|
|[CStringT:: FindOneOf](#findoneof)|Busca el primer carácter coincidente de un conjunto.|
|[CStringT:: Format](#format)|Da formato a la cadena como lo hace `sprintf`.|
|[CStringT:: FormatMessage](#formatmessage)|Da formato a una cadena de mensaje.|
|[CStringT:: FormatMessageV](#formatmessagev)|Da formato a una cadena de mensaje mediante una lista de argumentos de variable.|
|[CStringT:: FormatV](#formatv)|Da formato a la cadena mediante una lista variable de argumentos.|
|[CStringT:: GetEnvironmentVariable](#getenvironmentvariable)|Establece la cadena en el valor de la variable de entorno especificada.|
|[CStringT:: Insert](#insert)|Inserta un carácter individual o una subcadena en el índice especificado de la cadena.|
|[CStringT:: Left](#left)|Extrae la parte izquierda de una cadena.|
|[CStringT:: LoadString](#loadstring)|Carga un objeto de `CStringT` existente desde un recurso de Windows.|
|[CStringT:: MakeLower](#makelower)|Convierte todos los caracteres de esta cadena en caracteres en minúsculas.|
|[CStringT:: MakeReverse](#makereverse)|Invierte la cadena.|
|[CStringT:: MakeUpper](#makeupper)|Convierte todos los caracteres de esta cadena en caracteres en mayúsculas.|
|[CStringT:: MID](#mid)|Extrae la parte central de una cadena.|
|[CStringT:: OemToAnsi](#oemtoansi)|Realiza una conversión en contexto del juego de caracteres OEM en el juego de caracteres ANSI.|
|[CStringT:: Remove](#remove)|Quita los caracteres indicados de una cadena.|
|[CStringT:: Replace](#replace)|Reemplaza los caracteres indicados por otros caracteres.|
|[CStringT:: ReverseFind](#reversefind)|Busca un carácter dentro de una cadena más grande; comienza desde el final.|
|[CStringT:: Right](#right)|Extrae la parte derecha de una cadena.|
|[CStringT:: SetSysString](#setsysstring)|Establece un objeto BSTR existente con datos de un objeto `CStringT`.|
|[CStringT:: SpanExcluding](#spanexcluding)|Extrae los caracteres de la cadena, empezando por el primer carácter, que no están en el conjunto de caracteres identificados por `pszCharSet`.|
|[CStringT:: SpanIncluding](#spanincluding)|Extrae una subcadena que contiene solo los caracteres de un conjunto.|
|[CStringT:: Tokene](#tokenize)|Extrae los tokens especificados en una cadena de destino.|
|[CStringT:: Trim](#trim)|Recorta todos los caracteres de espacio en blanco iniciales y finales de la cadena.|
|[CStringT:: TrimLeft](#trimleft)|Recorta los caracteres de espacio en blanco iniciales de la cadena.|
|[CStringT:: TrimRight](#trimright)|Recorta los caracteres de espacio en blanco finales de la cadena.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[CStringT:: Operator =](#operator_eq)|Asigna un nuevo valor a un objeto `CStringT`.|
|[CStringT:: Operator +](#operator_add)|Concatena dos cadenas o un carácter y una cadena.|
|[CStringT:: Operator + =](#operator_add_eq)|Concatena una nueva cadena al final de una cadena existente.|
|[CStringT:: Operator = =](#operator_eq_eq)|Determina si dos cadenas son lógicamente iguales.|
|[CStringT:: Operator! =](#operator_neq)|Determina si dos cadenas no son iguales lógicamente.|
|[CStringT:: Operator &lt;](#operator_lt)|Determina si la cadena del lado izquierdo del operador es menor que la cadena del lado derecho.|
|[CStringT:: Operator &gt;](#operator_gt)|Determina si la cadena del lado izquierdo del operador es mayor que la cadena del lado derecho.|
|[CStringT:: Operator &lt;=](#operator_lt_eq)|Determina si la cadena del lado izquierdo del operador es menor o igual que la cadena del lado derecho.|
|[CStringT:: Operator &gt;=](#operator_gt_eq)|Determina si la cadena del lado izquierdo del operador es mayor o igual que la cadena del lado derecho.|

## <a name="remarks"></a>Observaciones

`CStringT` hereda de la [clase CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md). Las características avanzadas, como la manipulación de caracteres, la ordenación y la búsqueda, se implementan mediante `CStringT`.

> [!NOTE]
> `CStringT` objetos pueden producir excepciones. Esto se produce cuando un objeto de `CStringT` se queda sin memoria por cualquier motivo.

Un objeto `CStringT` consta de una secuencia de caracteres de longitud variable. `CStringT` proporciona funciones y operadores con una sintaxis similar a la de Basic. Los operadores de concatenación y comparación, junto con la administración de memoria simplificada, facilitan el uso de `CStringT` objetos que las matrices de caracteres normales.

> [!NOTE]
>  Aunque es posible crear instancias de `CStringT` que contengan caracteres nulos incrustados, le recomendamos que lo permitan. Llamar a métodos y operadores en `CStringT` objetos que contengan caracteres nulos incrustados puede producir resultados imprevistos.

Mediante el uso de diferentes combinaciones de los parámetros `BaseType` y `StringTraits`, `CStringT` objetos pueden incluirse en los tipos siguientes, que se han predefinido por las bibliotecas ATL.

Si se usa en una aplicación ATL:

`CString`, `CStringA`y `CStringW` se exportan desde el archivo DLL de MFC (MFC90. DLL), nunca desde archivos dll de usuario. Esto se hace para evitar que se defina la multiplicación de `CStringT`.

> [!NOTE]
>  Si el código contiene la solución alternativa para los errores del vinculador que se describe en [exportación de clases de cadena mediante CStringT](../../atl-mfc-shared/exporting-string-classes-using-cstringt.md), debe quitar ese código. Ya no es necesario.

Los siguientes tipos de cadena están disponibles en las aplicaciones basadas en MFC:

|CStringT (tipo)|Declaración|
|-------------------|-----------------|
|`CStringA`|Cadena de tipo de carácter ANSI compatible con CRT.|
|`CStringW`|Cadena de tipo de carácter Unicode compatible con CRT.|
|`CString`|Tipos de caracteres ANSI y Unicode compatibles con CRT.|

Los siguientes tipos de cadena están disponibles en los proyectos donde se define ATL_CSTRING_NO_CRT:

|CStringT (tipo)|Declaración|
|-------------------|-----------------|
|`CAtlStringA`|Cadena de tipo de carácter ANSI sin compatibilidad con CRT.|
|`CAtlStringW`|Cadena de tipo de carácter Unicode sin compatibilidad con CRT.|
|`CAtlString`|Tipos de caracteres ANSI y Unicode sin compatibilidad con CRT.|

Los siguientes tipos de cadena están disponibles en los proyectos en los que no se ha definido ATL_CSTRING_NO_CRT:

|CStringT (tipo)|Declaración|
|-------------------|-----------------|
|`CAtlStringA`|Cadena de tipo de carácter ANSI compatible con CRT.|
|`CAtlStringW`|Cadena de tipo de carácter Unicode compatible con CRT.|
|`CAtlString`|Tipos de caracteres ANSI y Unicode compatibles con CRT.|

`CString` objetos también tienen las siguientes características:

- `CStringT` objetos pueden crecer como resultado de las operaciones de concatenación.

- `CStringT` objetos siguen "semántica de valores". Piense en un objeto `CStringT` como una cadena real, no como un puntero a una cadena.

- Puede sustituir libremente `CStringT` objetos por `PCXSTR` argumentos de la función.

- Administración de memoria personalizada para búferes de cadena. Para obtener más información, vea [Administración de memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="cstringt-predefined-types"></a>Tipos predefinidos de CStringT

Dado que `CStringT` usa un argumento de plantilla para definir el tipo de carácter (ya sea [wchar_t](../../c-runtime-library/standard-types.md) o [Char](../../c-runtime-library/standard-types.md)) admitido, los tipos de parámetro de método pueden ser complicados en ocasiones. Para simplificar este problema, se define un conjunto de tipos predefinidos y se utiliza en toda la clase `CStringT`. En la tabla siguiente se enumeran los distintos tipos:

|Nombre|Descripción|
|----------|-----------------|
|`XCHAR`|Un único carácter (ya sea **wchar_t** o **Char**) con el mismo tipo de carácter que el objeto `CStringT`.|
|`YCHAR`|Un único carácter ( **wchar_t** o **Char**) con el tipo de carácter opuesto como el objeto `CStringT`.|
|`PXSTR`|Puntero a una cadena de caracteres ( **wchar_t** o **Char**) con el mismo tipo de carácter que el objeto `CStringT`.|
|`PYSTR`|Puntero a una cadena de caracteres ( **wchar_t** o **Char**) con el tipo de carácter opuesto como el objeto `CStringT`.|
|`PCXSTR`|Puntero a una cadena de caracteres **const** ( **wchar_t** o **Char**) con el mismo tipo de carácter que el objeto `CStringT`.|
|`PCYSTR`|Puntero a una cadena de caracteres **const** ( **wchar_t** o **Char**) con el tipo de carácter opuesto como el objeto `CStringT`.|

> [!NOTE]
>  El código que usaba previamente métodos no documentados de `CString` (como `AssignCopy`) debe reemplazarse por código que utiliza los siguientes métodos documentados de `CStringT` (como `GetBuffer` o `ReleaseBuffer`). Estos métodos se heredan de `CSimpleStringT`.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)

`CStringT`

## <a name="requirements"></a>Requisitos

|Encabezado|Se usa para|
|------------|-------------|
|cstringt.h|Objetos de cadena solo de MFC|
|atlstr.h|Objetos de cadena que no son de MFC|

##  <a name="allocsysstring"></a>CStringT:: AllocSysString

Asigna una cadena compatible con Automation del tipo BSTR y copia en ella el contenido del objeto `CStringT`, incluido el carácter nulo de terminación.

```
BSTR AllocSysString() const;
```

### <a name="return-value"></a>Valor devuelto

Cadena recién asignada.

### <a name="remarks"></a>Observaciones

En los programas MFC, se produce una [clase CMemoryException](../../mfc/reference/cmemoryexception-class.md) si no hay suficiente memoria. En los programas ATL, se produce una [CAtlException](../../atl/reference/catlexception-class.md) . Esta función se utiliza normalmente para devolver cadenas para la automatización.

Normalmente, si esta cadena se pasa a una función COM como parámetro [in], esto requiere que el autor de la llamada libere la cadena. Esto se puede hacer utilizando [SysFreeString](/windows/win32/api/oleauto/nf-oleauto-sysfreestring), tal como se describe en el Windows SDK. Para obtener más información, vea [asignar y liberar memoria para un BSTR](../../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md).

Para obtener más información sobre las funciones de asignación OLE en Windows, vea [SysAllocString](/windows/win32/api/oleauto/nf-oleauto-sysallocstring) en el Windows SDK.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CStringT::AllocSysString`.

[!code-cpp[NVC_ATLMFC_Utilities#105](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_1.cpp)]

##  <a name="ansitooem"></a>CStringT:: AnsiToOem

Convierte todos los caracteres de este objeto `CStringT` del juego de caracteres ANSI al Juego de caracteres OEM.

```
void AnsiToOem();
```

### <a name="remarks"></a>Observaciones

La función no está disponible si se define _UNICODE.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#106](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_2.cpp)]

##  <a name="appendformat"></a>CStringT:: AppendFormat

Anexa datos con formato a un objeto de `CStringT` existente.

```
void __cdecl AppendFormat(PCXSTR pszFormat, [, argument] ...);
void __cdecl AppendFormat(UINT nFormatID, [, argument] ...);
```

### <a name="parameters"></a>Parámetros

*pszFormat*<br/>
Cadena de control de formato.

*nFormatID*<br/>
Identificador de recurso de cadena que contiene la cadena de control de formato.

*argument*<br/>
Argumentos opcionales.

### <a name="remarks"></a>Observaciones

Esta función da formato y anexa una serie de caracteres y valores en el `CStringT`. Cada argumento opcional (si existe) se convierte y se anexa según la especificación de formato correspondiente en *pszFormat* o desde el recurso de cadena identificado por *nFormatID*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#107](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_3.cpp)]

##  <a name="collate"></a>CStringT:: COLLATE

Compara dos cadenas mediante la función de texto genérico `_tcscoll`.

```
int Collate(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parámetros

*psz*<br/>
La otra cadena utilizada para la comparación.

### <a name="return-value"></a>Valor devuelto

Cero si las cadenas son idénticas, < 0 si este `CStringT` objeto es menor que *PSZ*o > 0 si el objeto `CStringT` es mayor que *PSZ*.

### <a name="remarks"></a>Observaciones

La función de texto genérico `_tcscoll`, que se define en TCHAR. H, se asigna a `strcoll`, `wcscoll`o `_mbscoll`, dependiendo del juego de caracteres definido en tiempo de compilación. Cada función realiza una comparación con distinción entre mayúsculas y minúsculas de las cadenas según la página de códigos actualmente en uso. Para obtener más información, consulte [strcoll (, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md).

##  <a name="collatenocase"></a>CStringT:: CollateNoCase

Compara dos cadenas mediante la función de texto genérico `_tcscoll`.

```
int CollateNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parámetros

*psz*<br/>
La otra cadena utilizada para la comparación.

### <a name="return-value"></a>Valor devuelto

Cero si las cadenas son idénticas (sin distinción de mayúsculas y minúsculas), < 0 si este `CStringT` objeto es menor que *PSZ* (sin distinción de mayúsculas y minúsculas) o > 0 si este `CStringT` objeto es mayor que *PSZ* (sin distinción de mayúsculas y minúsculas).

### <a name="remarks"></a>Observaciones

La función de texto genérico `_tcscoll`, que se define en TCHAR. H, se asigna a `stricoll`, `wcsicoll`o `_mbsicoll`, dependiendo del juego de caracteres definido en tiempo de compilación. Cada función realiza una comparación sin distinción entre mayúsculas y minúsculas de las cadenas, de acuerdo con la página de códigos actualmente en uso. Para obtener más información, consulte [strcoll (, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#109](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_4.cpp)]

##  <a name="compare"></a>CStringT:: Compare

Compara dos cadenas (distingue mayúsculas de minúsculas).

```
int Compare(PCXSTR psz) const;
```

### <a name="parameters"></a>Parámetros

*psz*<br/>
La otra cadena utilizada para la comparación.

### <a name="return-value"></a>Valor devuelto

Cero si las cadenas son idénticas, < 0 si este `CStringT` objeto es menor que *PSZ*o > 0 si el objeto `CStringT` es mayor que *PSZ*.

### <a name="remarks"></a>Observaciones

La función de texto genérico `_tcscmp`, que se define en TCHAR. H, se asigna a `strcmp`, `wcscmp`o `_mbscmp`, dependiendo del juego de caracteres definido en tiempo de compilación. Cada función realiza una comparación con distinción entre mayúsculas y minúsculas de las cadenas y no se ve afectada por la configuración regional. Para obtener más información, vea [strcmp, wcscmp, _mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md).

Si la cadena contiene valores NULL incrustados, a efectos de la comparación, se considera que la cadena está truncada en el primer carácter nulo incrustado.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CStringT::Compare`.

[!code-cpp[NVC_ATLMFC_Utilities#110](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_5.cpp)]

##  <a name="comparenocase"></a>CStringT:: CompareNoCase

Compara dos cadenas (no distingue mayúsculas de minúsculas).

```
int CompareNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parámetros

*psz*<br/>
La otra cadena utilizada para la comparación.

### <a name="return-value"></a>Valor devuelto

Cero si las cadenas son idénticas (sin distinción de mayúsculas y minúsculas), < 0 si este `CStringT` objeto es menor que *PSZ* (sin distinción de mayúsculas y minúsculas) o > 0 si este `CStringT` objeto es mayor que *PSZ* (sin distinción de mayúsculas y minúsculas).

### <a name="remarks"></a>Observaciones

La función de texto genérico `_tcsicmp`, que se define en TCHAR. H, se asigna a `_stricmp`, `_wcsicmp` o `_mbsicmp`, dependiendo del juego de caracteres definido en tiempo de compilación. Cada función realiza una comparación sin distinción entre mayúsculas y minúsculas de las cadenas. La comparación depende del aspecto LC_CTYPE de la configuración regional, pero no LC_COLLATE. Para obtener más información, vea [_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#111](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_6.cpp)]

##  <a name="cstringt"></a>CStringT:: CStringT

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

*encabezado*<br/>
Puntero a una matriz de caracteres de longitud *nLength*, no terminada en NULL.

*nLength*<br/>
Recuento del número de caracteres de *PCH*.

*Cam*<br/>
Un solo carácter.

*pszSrc*<br/>
Una cadena terminada en null que se va a copiar en este objeto `CStringT`.

*pStringMgr*<br/>
Puntero al administrador de memoria para el objeto de `CStringT`. Para obtener más información sobre la `IAtlStringMgr` y la administración de memoria para `CStringT`, vea [Administración de memoria con CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

*strSrc*<br/>
Objeto de `CStringT` existente que se va a copiar en este objeto `CStringT`. Para obtener más información sobre `CThisString` y `CThisSimpleString`, vea la sección Comentarios.

*varSrc*<br/>
Objeto Variant que se va a copiar en este objeto `CStringT`.

*BaseType*<br/>
Tipo de carácter de la clase String. Puede ser uno de los siguientes:

**Char** (para cadenas de caracteres ANSI).

**wchar_t** (para cadenas de caracteres Unicode).

TCHAR (para cadenas de caracteres ANSI y Unicode).

*bMFCDLL*<br/>
Valor booleano que especifica si el proyecto es un archivo DLL de MFC (TRUE) o no (FALSE).

*SystemString*<br/>
Debe ser `System::String`y el proyecto debe compilarse con/CLR.

*pString*<br/>
Identificador de un objeto de `CStringT`.

### <a name="remarks"></a>Observaciones

Dado que los constructores copian los datos de entrada en un nuevo almacenamiento asignado, debe tener en cuenta que pueden producirse excepciones de memoria. Tenga en cuenta que algunos de estos constructores actúan como funciones de conversión. Esto permite sustituir, por ejemplo, un LPTSTR en el que se espera un objeto de `CStringT`.

- `CStringT`(`LPCSTR` `lpsz`): construye un `CStringT` Unicode a partir de una cadena ANSI. También puede usar este constructor para cargar un recurso de cadena, tal como se muestra en el ejemplo siguiente.

- `CStringT(` `LPCWSTR` `lpsz`): construye un `CStringT` a partir de una cadena Unicode.

- `CStringT`(`const unsigned char*` `psz`): permite construir un `CStringT` de un puntero a un **carácter sin signo**.

> [!NOTE]
>  Defina la macro _CSTRING_DISABLE_NARROW_WIDE_CONVERSION para desactivar la conversión implícita de cadenas entre las cadenas ANSI y Unicode. La macro excluye de los constructores de compilación que admiten la conversión.

Tenga en cuenta que el parámetro *strSrc* puede ser un objeto `CStringT` o `CThisSimpleString`. Por `CStringT`, utilice una de sus creaciones de instancias predeterminadas (`CString`, `CStringA`o `CStringW`); para `CThisSimpleString`, utilice un puntero **this** . `CThisSimpleString` declara una instancia de la [clase CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), que es una clase de cadena menor con una funcionalidad menos integrada que la clase `CStringT`.

El operador de sobrecarga `CSimpleStringT<>&()` construye un objeto `CStringT` a partir de una declaración de `CSimpleStringT`.

> [!NOTE]
>  Aunque es posible crear instancias de `CStringT` que contengan caracteres nulos incrustados, le recomendamos que lo permitan. Llamar a métodos y operadores en `CStringT` objetos que contengan caracteres nulos incrustados puede producir resultados imprevistos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#112](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_7.cpp)]

##  <a name="_dtorcstringt"></a>CStringT:: ~ CStringT

Destruye el objeto `CStringT`.

```
~CStringT() throw();
```

### <a name="remarks"></a>Observaciones

Destruye el objeto `CStringT`.

##  <a name="delete"></a>CStringT::D iminar

Elimina un carácter o caracteres de una cadena a partir del carácter que se encuentra en el índice especificado.

```
int Delete(int iIndex, int nCount = 1);
```

### <a name="parameters"></a>Parámetros

*iIndex*<br/>
Índice de base cero del primer carácter del objeto `CStringT` que se va a eliminar.

*nCount*<br/>
Número de caracteres que se van a quitar.

### <a name="return-value"></a>Valor devuelto

Longitud de la cadena modificada.

### <a name="remarks"></a>Observaciones

Si *nCount* es mayor que la cadena, se quitará el resto de la cadena.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#113](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_8.cpp)]

```Output
Before: Soccer is best,
    but hockey is quicker!
After: Soccer best,
    but hockey is quicker!
```

##  <a name="find"></a>CStringT:: Find

Busca en esta cadena la primera coincidencia de un carácter o subcadena.

```
int Find(PCXSTR pszSub, int iStart=0) const throw();
int Find(XCHAR ch, int iStart=0) const throw();
```

### <a name="parameters"></a>Parámetros

*pszSub*<br/>
Subcadena que se va a buscar.

*iStart*<br/>
Índice del carácter de la cadena en la que se va a comenzar la búsqueda, o 0 para comenzar desde el principio.

*Cam*<br/>
Carácter único que se va a buscar.

### <a name="return-value"></a>Valor devuelto

Índice de base cero del primer carácter de este `CStringT` objeto que coincide con la subcadena o los caracteres solicitados; -1 si no se encuentra la subcadena o carácter.

### <a name="remarks"></a>Observaciones

La función se sobrecarga para aceptar ambos caracteres individuales (similar a la función en tiempo de ejecución `strchr`) y cadenas (similar a `strstr`).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#114](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_9.cpp)]

##  <a name="findoneof"></a>CStringT:: FindOneOf

Busca en esta cadena el primer carácter que coincide con cualquier carácter incluido en *pszCharSet*.

```
int FindOneOf(PCXSTR pszCharSet) const throw();
```

### <a name="parameters"></a>Parámetros

*pszCharSet*<br/>
Cadena que contiene caracteres para buscar coincidencias.

### <a name="return-value"></a>Valor devuelto

Índice de base cero del primer carácter de esta cadena que también está en *pszCharSet*; -1 si no hay ninguna coincidencia.

### <a name="remarks"></a>Observaciones

Busca la primera aparición de cualquiera de los caracteres de *pszCharSet*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#115](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_10.cpp)]

##  <a name="format"></a>CStringT:: Format

Escribe datos con formato en un `CStringT` de la misma manera que [sprintf_s](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md) da formato a los datos en una matriz de caracteres de estilo C.

```
void __cdecl Format(UINT nFormatID, [, argument]...);
void __cdecl Format(PCXSTR pszFormat,  [, argument] ...);
```

### <a name="parameters"></a>Parámetros

*nFormatID*<br/>
Identificador de recurso de cadena que contiene la cadena de control de formato.

*pszFormat*<br/>
Cadena de control de formato.

*argument*<br/>
Argumentos opcionales.

### <a name="remarks"></a>Observaciones

Esta función da formato y almacena una serie de caracteres y valores en el `CStringT`. Cada argumento opcional (si existe) se convierte y se genera de acuerdo con la especificación de formato correspondiente en *pszFormat* o desde el recurso de cadena identificado por *nFormatID*.

Se producirá un error en la llamada si el propio objeto de cadena se ofrece como parámetro para `Format`. Por ejemplo, el código siguiente producirá resultados imprevisibles:

[!code-cpp[NVC_ATLMFC_Utilities#116](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_11.cpp)]

Para obtener más información, vea [Sintaxis de especificación de formato: Funciones printf y wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#117](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_12.cpp)]

##  <a name="formatmessage"></a>CStringT:: FormatMessage

Da formato a una cadena de mensaje.

```
void __cdecl FormatMessage(UINT nFormatID, [, argument]...);
void __cdecl FormatMessage(PCXSTR pszFormat, [, argument]...);
```

### <a name="parameters"></a>Parámetros

*nFormatID*<br/>
Identificador de recurso de cadena que contiene el texto del mensaje sin formato.

*pszFormat*<br/>
Apunta a la cadena de control de formato. Se examinará en busca de inserciones y se le aplicará el formato correspondiente. La cadena de formato es similar a las cadenas de formato de estilo *printf*de la función en tiempo de ejecución, salvo que permite que los parámetros se inserten en un orden arbitrario.

*argument*<br/>
Argumentos opcionales.

### <a name="remarks"></a>Observaciones

La función requiere una definición de mensaje como entrada. La definición del mensaje viene determinada por *pszFormat* o por el recurso de cadena identificado por *nFormatID*. La función copia el texto del mensaje con formato en el objeto de `CStringT`, procesando las secuencias de inserción incrustadas si se solicitan.

> [!NOTE]
> `FormatMessage` intenta asignar la memoria del sistema para la cadena con el nuevo formato. Si se produce un error en este intento, se produce automáticamente una excepción de memoria.

Cada inserción debe tener un parámetro correspondiente después del parámetro *pszFormat* o *nFormatID* . En el texto del mensaje, se admiten varias secuencias de escape para dar formato al mensaje de forma dinámica. Para obtener más información, vea la función [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) de Windows en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#118](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_13.cpp)]

##  <a name="formatmessagev"></a>CStringT:: FormatMessageV

Da formato a una cadena de mensaje mediante una lista de argumentos de variable.

```
void FormatMessageV(PCXSTR pszFormat, va_list* pArgList);
```

### <a name="parameters"></a>Parámetros

*pszFormat*<br/>
Apunta a la cadena de control de formato. Se examinará en busca de inserciones y se le aplicará el formato correspondiente. La cadena de formato es similar a las cadenas de formato de `printf`de la función en tiempo de ejecución, salvo que permite que los parámetros se inserten en un orden arbitrario.

*pArgList*<br/>
Puntero a una lista de argumentos.

### <a name="remarks"></a>Observaciones

La función requiere una definición de mensaje como entrada, determinada por *pszFormat*. La función copia el texto del mensaje con formato y una lista variable de argumentos en el objeto `CStringT`, procesando las secuencias Insert incrustadas si se solicitan.

> [!NOTE]
> `FormatMessageV` llama a [CStringT:: FormatMessage](#formatmessage), que intenta asignar la memoria del sistema para la cadena con el nuevo formato. Si se produce un error en este intento, se produce automáticamente una excepción de memoria.

Para obtener más información, vea la función [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) de Windows en el Windows SDK.

##  <a name="formatv"></a>CStringT:: FormatV

Da formato a una cadena de mensaje mediante una lista de argumentos de variable.

```
void FormatV(PCXSTR pszFormat, va_list args);
```

### <a name="parameters"></a>Parámetros

*pszFormat*<br/>
Apunta a la cadena de control de formato. Se examinará en busca de inserciones y se le aplicará el formato correspondiente. La cadena de formato es similar a las cadenas de formato de `printf`de la función en tiempo de ejecución, salvo que permite que los parámetros se inserten en un orden arbitrario.

*args*<br/>
Puntero a una lista de argumentos.

### <a name="remarks"></a>Observaciones

Escribe una cadena con formato y una lista variable de argumentos en una cadena de `CStringT` de la misma manera que `vsprintf_s` da formato a los datos en una matriz de caracteres de estilo C.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#119](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_14.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#120](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_15.cpp)]

##  <a name="getenvironmentvariable"></a>CStringT:: GetEnvironmentVariable

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

Recupera el valor de la variable especificada del bloque de entorno del proceso de llamada. El valor está en forma de una cadena de caracteres terminada en NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#121](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_16.cpp)]

##  <a name="insert"></a>CStringT:: Insert

Inserta un carácter individual o una subcadena en el índice especificado de la cadena.

```
int Insert(int iIndex, PCXSTR psz);
int Insert(int iIndex, XCHAR ch);
```

### <a name="parameters"></a>Parámetros

*iIndex*<br/>
Índice del carácter antes del cual se llevará a cabo la inserción.

*psz*<br/>
Puntero a la subcadena que se va a insertar.

*Cam*<br/>
Carácter que se va a insertar.

### <a name="return-value"></a>Valor devuelto

Longitud de la cadena modificada.

### <a name="remarks"></a>Observaciones

El parámetro *iIndex* identifica el primer carácter que se va a colocar para dejar espacio para el carácter o subcadena. Si *NINDEX* es cero, la inserción se realizará antes de la cadena completa. Si *NINDEX* es mayor que la longitud de la cadena, la función concatenará la cadena actual y el nuevo material proporcionado por *CH* o *PSZ*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#122](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_17.cpp)]

##  <a name="left"></a>CStringT:: Left

Extrae los caracteres *nCount* situados más a la izquierda de este objeto `CStringT` y devuelve una copia de la subcadena extraída.

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

En el caso de los juegos de caracteres multibyte (MBCS), *nCount* trata cada secuencia de 8 bits como un carácter, de modo que *nCount* devuelve el número de caracteres de varios bytes multiplicado por dos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#123](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_18.cpp)]

##  <a name="loadstring"></a>CStringT:: LoadString

Lee un recurso de cadena de Windows, identificado por *nID*, en un objeto de `CStringT` existente.

```
BOOL LoadString(HINSTANCE hInstance, UINT nID, WORD wLanguageID);
BOOL LoadString(HINSTANCE hInstance, UINT nID);
BOOL LoadString(UINT nID);
```

### <a name="parameters"></a>Parámetros

*hInstance*<br/>
Identificador de la instancia del módulo.

*nID*<br/>
IDENTIFICADOR de recurso de cadena de Windows.

*wLanguageID*<br/>
Lenguaje del recurso de cadena.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la carga de recursos se realizó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Carga el recurso de cadena (*nID*) desde el módulo especificado (*hInstance*) mediante el lenguaje especificado (*wLanguage*).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#124](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_19.cpp)]

##  <a name="makelower"></a>CStringT:: MakeLower

Convierte el objeto de `CStringT` en una cadena en minúsculas.

```
CStringT& MakeLower();
```

### <a name="return-value"></a>Valor devuelto

Cadena en minúsculas resultante.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#125](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_20.cpp)]

##  <a name="makereverse"></a>CStringT:: MakeReverse

Invierte el orden de los caracteres en el objeto de `CStringT`.

```
CStringT& MakeReverse();
```

### <a name="return-value"></a>Valor devuelto

Cadena invertida resultante.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#126](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_21.cpp)]

##  <a name="makeupper"></a>CStringT:: MakeUpper

Convierte el objeto de `CStringT` en una cadena en mayúsculas.

```
CStringT& MakeUpper();
```

### <a name="return-value"></a>Valor devuelto

Cadena resultante en mayúsculas.

### <a name="remarks"></a>Observaciones

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#127](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_22.cpp)]

##  <a name="mid"></a>CStringT:: MID

Extrae una subcadena de caracteres *nCount* de este objeto `CStringT`, comenzando en la posición *iFirst* (basada en cero).

```
CStringT Mid(int iFirst, int nCount) const;
CStringT Mid(int iFirst) const;
```

### <a name="parameters"></a>Parámetros

*iFirst*<br/>
Índice de base cero del primer carácter de este objeto `CStringT` que se va a incluir en la subcadena extraída.

*nCount*<br/>
Número de caracteres que se va a extraer de este objeto `CStringT`. Si no se proporciona este parámetro, se extrae el resto de la cadena.

### <a name="return-value"></a>Valor devuelto

El objeto `CStringT` que contiene una copia del rango de caracteres especificado. Tenga en cuenta que el objeto de `CStringT` devuelto puede estar vacío.

### <a name="remarks"></a>Observaciones

La función devuelve una copia de la subcadena extraída. `Mid` es similar a la función Mid básica (salvo que los índices de Basic se basan en uno).

En el caso de los juegos de caracteres multibyte (MBCS), *nCount* hace referencia a cada carácter de 8 bits; es decir, un byte inicial y final de un carácter multibyte se cuentan como dos caracteres.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#128](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_23.cpp)]

##  <a name="oemtoansi"></a>CStringT:: OemToAnsi

Convierte todos los caracteres de este `CStringT` objeto del juego de caracteres OEM en el juego de caracteres ANSI.

```
void OemToAnsi();
```

### <a name="remarks"></a>Observaciones

Esta función no está disponible si se define _UNICODE.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CStringT:: AnsiToOem](#ansitooem).

##  <a name="operator_eq"></a>CStringT:: Operator =

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
`CStringT` que se va a asignar a esta cadena.

*str*<br/>
Referencia a un objeto `CThisSimpleString`.

*bMFCDLL*<br/>
Un valor booleano que especifica si el proyecto es un archivo DLL de MFC o no.

*BaseType*<br/>
Tipo base de cadena.

*var*<br/>
Objeto Variant que se va a asignar a esta cadena.

*Cam*<br/>
Carácter ANSI o Unicode que se va a asignar a la cadena.

*pszSrc*<br/>
Puntero a la cadena original que se va a asignar.

### <a name="remarks"></a>Observaciones

El operador de asignación acepta otro objeto `CStringT`, un puntero de carácter o un solo carácter. Debe tener en cuenta que se pueden producir excepciones de memoria cada vez que se usa este operador, ya que se puede asignar un nuevo almacenamiento.

Para obtener información sobre `CThisSimpleString`, vea la sección Comentarios de [CStringT:: CStringT](#cstringt).

> [!NOTE]
> Aunque es posible crear instancias de `CStringT` que contengan caracteres nulos incrustados, le recomendamos que lo permitan. Llamar a métodos y operadores en `CStringT` objetos que contengan caracteres nulos incrustados puede producir resultados imprevistos.

##  <a name="operator_add"></a>CStringT:: Operator +

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
Carácter ANSI o Unicode que se va a concatenar con una cadena.

*CH2*<br/>
Carácter ANSI o Unicode que se va a concatenar con una cadena.

*Str1*<br/>
`CStringT` que se va a concatenar con una cadena o un carácter.

*str2*<br/>
`CStringT` que se va a concatenar con una cadena o un carácter.

*psz1*<br/>
Puntero a una cadena terminada en null que se va a concatenar con una cadena o un carácter.

*psz2*<br/>
Puntero a una cadena que se va a concatenar con una cadena o un carácter.

### <a name="remarks"></a>Observaciones

Hay siete formas de sobrecarga de la función `CStringT::operator+`. La primera versión concatena dos objetos `CStringT` existentes. Los dos siguientes concatenan un objeto `CStringT` y una cadena terminada en NULL. Los dos siguientes concatenan un objeto `CStringT` y un carácter ANSI. Los dos últimos concatenan un objeto `CStringT` y un carácter Unicode.

> [!NOTE]
>  Aunque es posible crear instancias de `CStringT` que contengan caracteres nulos incrustados, le recomendamos que lo permitan. Llamar a métodos y operadores en `CStringT` objetos que contengan caracteres nulos incrustados puede producir resultados imprevistos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#140](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_24.cpp)]

##  <a name="operator_add_eq"></a>CStringT:: Operator + =

Concatena caracteres al final de la cadena.

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

*str*<br/>
Referencia a un objeto `CThisSimpleString`.

*bMFCDLL*<br/>
Un valor booleano que especifica si el proyecto es un archivo DLL de MFC o no.

*BaseType*<br/>
Tipo base de cadena.

*var*<br/>
Objeto Variant que se va a concatenar en esta cadena.

*Cam*<br/>
Carácter ANSI o Unicode que se va a concatenar con una cadena.

*pszSrc*<br/>
Puntero a la cadena original que se va a concatenar.

*strSrc*<br/>
`CStringT` que se va a concatenar a esta cadena.

### <a name="remarks"></a>Observaciones

El operador acepta otro objeto `CStringT`, un puntero de carácter o un carácter único. Debe tener en cuenta que se pueden producir excepciones de memoria cada vez que utilice este operador de concatenación porque se puede asignar un nuevo almacenamiento para los caracteres agregados a este objeto `CStringT`.

Para obtener información sobre `CThisSimpleString`, vea la sección Comentarios de [CStringT:: CStringT](#cstringt).

> [!NOTE]
>  Aunque es posible crear instancias de `CStringT` que contengan caracteres nulos incrustados, le recomendamos que lo permitan. Llamar a métodos y operadores en `CStringT` objetos que contengan caracteres nulos incrustados puede producir resultados imprevistos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#141](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_25.cpp)]

##  <a name="operator_eq_eq"></a>CStringT:: Operator = =

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
Carácter ANSI o Unicode para la comparación.

*CH2*<br/>
Carácter ANSI o Unicode para la comparación.

*Str1*<br/>
`CStringT` para la comparación.

*str2*<br/>
`CStringT` para la comparación.

*psz1*<br/>
Puntero a una cadena terminada en null para la comparación.

*psz2*<br/>
Puntero a una cadena terminada en null para la comparación.

### <a name="remarks"></a>Observaciones

Comprueba si una cadena o un carácter del lado izquierdo es igual a una cadena o carácter del lado derecho y devuelve TRUE o FALSE en consecuencia.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#142](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_26.cpp)]

##  <a name="operator_neq"></a>CStringT:: Operator! =

Determina si dos cadenas no son iguales lógicamente.

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
Carácter ANSI o Unicode que se va a concatenar con una cadena.

*CH2*<br/>
Carácter ANSI o Unicode que se va a concatenar con una cadena.

*Str1*<br/>
`CStringT` para la comparación.

*str2*<br/>
`CStringT` para la comparación.

*psz1*<br/>
Puntero a una cadena terminada en null para la comparación.

*psz2*<br/>
Puntero a una cadena terminada en null para la comparación.

### <a name="remarks"></a>Observaciones

Comprueba si una cadena o un carácter del lado izquierdo no es igual a una cadena o carácter del lado derecho.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#143](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_27.cpp)]

##  <a name="operator_lt"></a>CStringT:: Operator &lt;

Determina si la cadena del lado izquierdo del operador es menor que la cadena del lado derecho.

```
friend bool operator<(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parámetros

*Str1*<br/>
`CStringT` para la comparación.

*str2*<br/>
`CStringT` para la comparación.

*psz1*<br/>
Puntero a una cadena terminada en null para la comparación.

*psz2*<br/>
Puntero a una cadena terminada en null para la comparación.

### <a name="remarks"></a>Observaciones

Una comparación lexicográfica entre cadenas, carácter a carácter hasta que:

- Encuentra dos caracteres correspondientes distintos y el resultado de la comparación se toma como el resultado de la comparación entre las cadenas.

- No encuentra ninguna desigualdad, pero una cadena tiene más caracteres que la otra y la cadena más corta se considera menor que la cadena más larga.

- No encuentra ninguna desigualdad y encuentra que las cadenas tienen el mismo número de caracteres, por lo que las cadenas son iguales.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#144](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_28.cpp)]

##  <a name="operator_gt"></a>CStringT:: Operator &gt;

Determina si la cadena del lado izquierdo del operador es mayor que la cadena del lado derecho.

```
friend bool operator>(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parámetros

*Str1*<br/>
`CStringT` para la comparación.

*str2*<br/>
`CStringT` para la comparación.

*psz1*<br/>
Puntero a una cadena terminada en null para la comparación.

*psz2*<br/>
Puntero a una cadena terminada en null para la comparación.

### <a name="remarks"></a>Observaciones

Una comparación lexicográfica entre cadenas, carácter a carácter hasta que:

- Encuentra dos caracteres correspondientes distintos y el resultado de la comparación se toma como el resultado de la comparación entre las cadenas.

- No encuentra ninguna desigualdad, pero una cadena tiene más caracteres que la otra y la cadena más corta se considera menor que la cadena más larga.

- No encuentra ninguna desigualdad y encuentra que las cadenas tienen el mismo número de caracteres, por lo que las cadenas son iguales.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#145](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_29.cpp)]

##  <a name="operator_lt_eq"></a>CStringT:: Operator &lt;=

Determina si la cadena del lado izquierdo del operador es menor o igual que la cadena del lado derecho.

```
friend bool operator<=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parámetros

*Str1*<br/>
`CStringT` para la comparación.

*str2*<br/>
`CStringT` para la comparación.

*psz1*<br/>
Puntero a una cadena terminada en null para la comparación.

*psz2*<br/>
Puntero a una cadena terminada en null para la comparación.

### <a name="remarks"></a>Observaciones

Una comparación lexicográfica entre cadenas, carácter a carácter hasta que:

- Encuentra dos caracteres correspondientes distintos y el resultado de la comparación se toma como el resultado de la comparación entre las cadenas.

- No encuentra ninguna desigualdad, pero una cadena tiene más caracteres que la otra y la cadena más corta se considera menor que la cadena más larga.

- No encuentra ninguna desigualdad y encuentra que las cadenas tienen el mismo número de caracteres, por lo que las cadenas son iguales.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#146](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_30.cpp)]

##  <a name="operator_gt_eq"></a>CStringT:: Operator &gt;=

Determina si la cadena del lado izquierdo del operador es mayor o igual que la cadena del lado derecho.

```
friend bool operator>=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parámetros

*Str1*<br/>
`CStringT` para la comparación.

*str2*<br/>
`CStringT` para la comparación.

*psz1*<br/>
Puntero a una cadena para la comparación.

*psz2*<br/>
Puntero a una cadena para la comparación.

### <a name="remarks"></a>Observaciones

Una comparación lexicográfica entre cadenas, carácter a carácter hasta que:

- Encuentra dos caracteres correspondientes distintos y el resultado de la comparación se toma como el resultado de la comparación entre las cadenas.

- No encuentra ninguna desigualdad, pero una cadena tiene más caracteres que la otra y la cadena más corta se considera menor que la cadena más larga.

- No encuentra ninguna desigualdad y encuentra que las cadenas tienen el mismo número de caracteres, por lo que las cadenas son iguales.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#147](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_31.cpp)]

##  <a name="remove"></a>CStringT:: Remove

Quita todas las instancias del carácter especificado de la cadena.

```
int Remove(XCHAR chRemove);
```

### <a name="parameters"></a>Parámetros

*chRemove*<br/>
Carácter que se va a quitar de una cadena.

### <a name="return-value"></a>Valor devuelto

Recuento de caracteres que se han quitado de la cadena. Cero si no se cambia la cadena.

### <a name="remarks"></a>Observaciones

Las comparaciones del carácter distinguen mayúsculas de minúsculas.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#129](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_32.cpp)]

##  <a name="replace"></a>CStringT:: Replace

Hay dos versiones de `Replace`. La primera versión reemplaza una o más copias de una subcadena con otra subcadena. Ambas subcadenas están terminadas en NULL. La segunda versión reemplaza una o más copias de un carácter mediante otro carácter. Ambas versiones operan en los datos de caracteres almacenados en `CStringT`.

```
int Replace(PCXSTR pszOld, PCXSTR pszNew);
int Replace(XCHAR chOld, XCHAR chNew);
```

### <a name="parameters"></a>Parámetros

*pszOld*<br/>
Puntero a una cadena terminada en null que se va a reemplazar por *pszNew*.

*pszNew*<br/>
Puntero a una cadena terminada en null que reemplaza a *pszOld*.

*chOld*<br/>
Carácter que se va a reemplazar por *chNew*.

*chNew*<br/>
Carácter que reemplaza a *chOld*.

### <a name="return-value"></a>Valor devuelto

Devuelve el número de instancias reemplazadas del carácter o subcadena, o cero si no se cambia la cadena.

### <a name="remarks"></a>Observaciones

`Replace` puede cambiar la longitud de la cadena porque *pszNew* y *pszOld* no tienen que tener la misma longitud, y se pueden cambiar varias copias de la subcadena antigua a la nueva. La función realiza una coincidencia que distingue entre mayúsculas y minúsculas.

Ejemplos de instancias de `CStringT` son `CString`, `CStringA`y `CStringW`.

Por `CStringA`, `Replace` funciona con caracteres ANSI o multibyte (MBCS). Por `CStringW`, `Replace` funciona con caracteres anchos.

Por `CString`, el tipo de datos de caracteres se selecciona en tiempo de compilación, en función de si se definen las constantes de la tabla siguiente.

|Constante definida|Tipo de datos de caracteres|
|----------------------|-------------------------|
|_UNICODE|Caracteres anchos|
|_MBCS|Caracteres de varios bytes|
|Neither|Caracteres de un solo byte|
|Ambos|No definido|

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#200](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_33.cpp)]

##  <a name="reversefind"></a>CStringT:: ReverseFind

Busca en este objeto de `CStringT` la última coincidencia de un carácter.

```
int ReverseFind(XCHAR ch) const throw();
```

### <a name="parameters"></a>Parámetros

*Cam*<br/>
Carácter que se va a buscar.

### <a name="return-value"></a>Valor devuelto

Índice de base cero del último carácter de este `CStringT` objeto que coincide con el carácter solicitado, o-1 si no se encuentra el carácter.

### <a name="remarks"></a>Observaciones

La función es similar a la función en tiempo de ejecución `strrchr`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#130](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_34.cpp)]

##  <a name="right"></a>CStringT:: Right

Extrae el último (es decir, el situado más a la derecha) *nCount* caracteres de este objeto `CStringT` y devuelve una copia de la subcadena extraída.

```
CStringT Right(int nCount) const;
```

### <a name="parameters"></a>Parámetros

*nCount*<br/>
Número de caracteres que se va a extraer de este objeto `CStringT`.

### <a name="return-value"></a>Valor devuelto

El objeto `CStringT` que contiene una copia del rango de caracteres especificado. Tenga en cuenta que el objeto de `CStringT` devuelto puede estar vacío.

### <a name="remarks"></a>Observaciones

Si *nCount* supera la longitud de la cadena, se extrae toda la cadena. `Right` es similar a la función de `Right` básica (salvo que los índices en Basic están basados en cero).

En el caso de los juegos de caracteres multibyte (MBCS), *nCount* hace referencia a cada carácter de 8 bits; es decir, un byte inicial y final de un carácter multibyte se cuentan como dos caracteres.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#131](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_35.cpp)]

##  <a name="setsysstring"></a>CStringT:: SetSysString

Reasigna el BSTR al que apunta *pbstr* y copia en él el contenido del objeto `CStringT`, incluido el carácter nulo.

```
BSTR SetSysString(BSTR* pbstr) const;
```

### <a name="parameters"></a>Parámetros

*pbstr*<br/>
Puntero a una cadena de caracteres.

### <a name="return-value"></a>Valor devuelto

La nueva cadena.

### <a name="remarks"></a>Observaciones

En función del contenido del objeto `CStringT`, puede cambiar el valor del BSTR al que hace referencia *pbstr* . La función produce una `CMemoryException` si no hay suficiente memoria.

Esta función se utiliza normalmente para cambiar el valor de las cadenas que se pasan por referencia para la automatización.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#132](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_36.cpp)]

##  <a name="spanexcluding"></a>CStringT:: SpanExcluding

Extrae los caracteres de la cadena, empezando por el primer carácter, que no están en el conjunto de caracteres identificados por *pszCharSet*.

```
CStringT SpanExcluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>Parámetros

*pszCharSet*<br/>
Cadena interpretada como un conjunto de caracteres.

### <a name="return-value"></a>Valor devuelto

Una subcadena que contiene los caracteres de la cadena que no están en *pszCharSet*, empezando por el primer carácter de la cadena y terminando por el primer carácter encontrado en la cadena que también está en *pszCharSet* (es decir, empezando por el primer carácter de la cadena y hasta el primer carácter de la cadena que se encuentra *pszCharSet*). Devuelve la cadena completa si no se encuentra ningún carácter en *pszCharSet* en la cadena.

### <a name="remarks"></a>Observaciones

`SpanExcluding` extrae y devuelve todos los caracteres que preceden a la primera aparición de un carácter de *pszCharSet* (es decir, no se devuelven el carácter de *pszCharSet* y todos los caracteres que siguen en la cadena). Si no se encuentra ningún carácter de *pszCharSet* en la cadena, `SpanExcluding` devuelve la cadena completa.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#133](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_37.cpp)]

##  <a name="spanincluding"></a>CStringT:: SpanIncluding

Extrae los caracteres de la cadena, empezando por el primer carácter, que se encuentran en el conjunto de caracteres identificados por *pszCharSet*.

```
CStringT SpanIncluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>Parámetros

*pszCharSet*<br/>
Cadena interpretada como un conjunto de caracteres.

### <a name="return-value"></a>Valor devuelto

Una subcadena que contiene los caracteres de la cadena que están en *pszCharSet*, empezando por el primer carácter de la cadena y finalizando cuando se encuentra un carácter en la cadena que no está en *pszCharSet*. `SpanIncluding` devuelve una subcadena vacía si el primer carácter de la cadena no está en el conjunto especificado.

### <a name="remarks"></a>Observaciones

Si el primer carácter de la cadena no está en el juego de caracteres, `SpanIncluding` devuelve una cadena vacía. De lo contrario, devuelve una secuencia de caracteres consecutivos que se encuentran en el conjunto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#134](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_38.cpp)]

##  <a name="tokenize"></a>CStringT:: Tokene

Busca el siguiente token en una cadena de destino.

```
CStringT Tokenize(PCXSTR pszTokens, int& iStart) const;
```

### <a name="parameters"></a>Parámetros

*pszTokens*<br/>
Cadena que contiene los delimitadores de token. El orden de estos delimitadores no es importante.

*iStart*<br/>
Índice de base cero en el que se va a iniciar la búsqueda.

### <a name="return-value"></a>Valor devuelto

Objeto `CStringT` que contiene el valor del token actual.

### <a name="remarks"></a>Observaciones

La función `Tokenize` busca el token siguiente en la cadena de destino. El conjunto de caracteres de *pszTokens* especifica los delimitadores posibles del token que se va a buscar. En cada llamada a `Tokenize` la función comienza en *iStart*, omite los delimitadores iniciales y devuelve un objeto `CStringT` que contiene el token actual, que es la cadena de caracteres hasta el siguiente carácter delimitador. El valor de *iStart* se actualiza para que sea la posición que sigue al carácter delimitador final o-1 si se alcanzó el final de la cadena. Se pueden separar más tokens del resto de la cadena de destino mediante una serie de llamadas a `Tokenize`, mediante *iStart* para realizar un seguimiento de dónde se leerá el token siguiente en la cadena. Cuando no hay más tokens, la función devolverá una cadena vacía y *iStart* se establecerá en-1.

A diferencia de las funciones de símbolo (token) de CRT, como [strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l](../../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md), `Tokenize` no modifica la cadena de destino.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#135](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_39.cpp)]

### <a name="remarks"></a>Observaciones

La salida de este ejemplo es la siguiente:

```Output
Resulting Token: First
Resulting Token: Second
Resulting Token: Third
```

##  <a name="trim"></a>CStringT:: Trim

Recorta los caracteres iniciales y finales de la cadena.

```
CStringT& Trim(XCHAR chTarget);
CStringT& Trim(PCXSTR pszTargets);
CStringT& Trim();
```

### <a name="parameters"></a>Parámetros

*chTarget*<br/>
Carácter de destino que se va a recortar.

*pszTargets*<br/>
Puntero a una cadena que contiene los caracteres de destino que se van a recortar. Todas las apariciones iniciales y finales de los caracteres de *pszTarget* se eliminarán del objeto `CStringT`.

### <a name="return-value"></a>Valor devuelto

Devuelve la cadena recortada.

### <a name="remarks"></a>Observaciones

Quita todas las apariciones iniciales y finales de una de las siguientes opciones:

- Carácter especificado por *chTarget*.

- Todos los caracteres que se encuentran en la cadena especificada por *pszTargets*.

- Eran.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#136](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_40.cpp)]

### <a name="remarks"></a>Observaciones

La salida de este ejemplo es la siguiente:

```Output
Before: "******Soccer is best, but liquor is quicker!!!!!"
After : "Soccer is best, but liquor is quicker"
```

##  <a name="trimleft"></a>CStringT:: TrimLeft

Recorta los caracteres iniciales de la cadena.

```
CStringT& TrimLeft(XCHAR chTarget);
CStringT& TrimLeft(PCXSTR pszTargets);
CStringT& TrimLeft();
```

### <a name="parameters"></a>Parámetros

*chTarget*<br/>
Carácter de destino que se va a recortar.

*pszTargets*<br/>
Puntero a una cadena que contiene los caracteres de destino que se van a recortar. Todas las apariciones iniciales de caracteres en *pszTarget* se eliminarán del objeto `CStringT`.

### <a name="return-value"></a>Valor devuelto

Cadena recortada resultante.

### <a name="remarks"></a>Observaciones

Quita todas las apariciones iniciales y finales de una de las siguientes opciones:

- Carácter especificado por *chTarget*.

- Todos los caracteres que se encuentran en la cadena especificada por *pszTargets*.

- Eran.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#137](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_41.cpp)]

##  <a name="trimright"></a>CStringT:: TrimRight

Recorta los caracteres finales de la cadena.

```
CStringT& TrimRight(XCHAR chTarget);
CStringT& TrimRight(PCXSTR pszTargets);
CStringT& TrimRight();
```

### <a name="parameters"></a>Parámetros

*chTarget*<br/>
Carácter de destino que se va a recortar.

*pszTargets*<br/>
Puntero a una cadena que contiene los caracteres de destino que se van a recortar. Todas las apariciones de caracteres finales de *pszTarget* se eliminarán del objeto `CStringT`.

### <a name="return-value"></a>Valor devuelto

Devuelve el objeto `CStringT` que contiene la cadena recortada.

### <a name="remarks"></a>Observaciones

Quita las apariciones finales de uno de los siguientes elementos:

- Carácter especificado por *chTarget*.

- Todos los caracteres que se encuentran en la cadena especificada por *pszTargets*.

- Eran.

La versión de `CStringT& TrimRight(XCHAR chTarget)` acepta un parámetro de carácter y quita todas las copias de ese carácter del final de los datos de cadena de `CStringT`. Comienza desde el final de la cadena y funciona hacia delante. Se detiene cuando encuentra un carácter diferente o cuando `CSTringT` se queda sin datos de caracteres.

La versión de `CStringT& TrimRight(PCXSTR pszTargets)` acepta una cadena terminada en null que contiene todos los caracteres que se van a buscar. Quita todas las copias de esos caracteres en el objeto `CStringT`. Se inicia al final de la cadena y funciona hacia delante. Se detiene cuando encuentra un carácter que no está en la cadena de destino, o cuando `CStringT` se queda sin datos de caracteres. No intenta hacer coincidir la cadena de destino completa con una subcadena al final de `CStringT`.

La versión `CStringT& TrimRight()` no requiere ningún parámetro. Recorta los caracteres de espacio en blanco finales del final de la cadena de `CStringT`. Los caracteres de espacio en blanco pueden ser saltos de línea, espacios o tabulaciones.

-

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#138](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_42.cpp)]

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases compartidas de ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)<br/>
[CSimpleStringT (clase)](../../atl-mfc-shared/reference/csimplestringt-class.md)
