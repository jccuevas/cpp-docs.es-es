---
title: Clase CDumpContext
ms.date: 11/04/2016
f1_keywords:
- CDumpContext
- AFX/CDumpContext
- AFX/CDumpContext::CDumpContext
- AFX/CDumpContext::DumpAsHex
- AFX/CDumpContext::Flush
- AFX/CDumpContext::GetDepth
- AFX/CDumpContext::HexDump
- AFX/CDumpContext::SetDepth
helpviewer_keywords:
- CDumpContext [MFC], CDumpContext
- CDumpContext [MFC], DumpAsHex
- CDumpContext [MFC], Flush
- CDumpContext [MFC], GetDepth
- CDumpContext [MFC], HexDump
- CDumpContext [MFC], SetDepth
ms.assetid: 98c52b2d-14b5-48ed-b423-479a4d1c60fa
ms.openlocfilehash: aa549e5347bf2bd357fa3c28e81a0309ea4f4aff
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374002"
---
# <a name="cdumpcontext-class"></a>Clase CDumpContext

Admite resultados de diagnóstico orientados a secuencia en forma de texto legible.

## <a name="syntax"></a>Sintaxis

```
class CDumpContext
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDumpContext::CDumpContext](#cdumpcontext)|Construye un objeto `CDumpContext`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDumpContext::DumpAsHex](#dumpashex)|Vuelca el elemento indicado en formato hexadecimal.|
|[CDumpContext::Flush](#flush)|Vacía los datos del búfer de contexto de volcado.|
|[CDumpContext::GetDepth](#getdepth)|Obtiene un entero correspondiente a la profundidad del volcado.|
|[CDumpContext::HexDump](#hexdump)|Vuelca bytes contenidos en una matriz en formato hexadecimal.|
|[CDumpContext::SetDepth](#setdepth)|Establece la profundidad del volcado.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDumpContext::operator&lt;&lt;](#operator_lt_lt)|Inserta variables y objetos en el contexto de volcado.|

## <a name="remarks"></a>Observaciones

`CDumpContext`no tiene una clase base.

Puede usar [afxDump](diagnostic-services.md#afxdump), `CDumpContext` un objeto declarado previamente, para la mayor parte del volcado. El `afxDump` objeto solo está disponible en la versión de depuración de la biblioteca Microsoft Foundation Class.

Varios de los servicios `afxDump` de [diagnóstico](../../mfc/reference/diagnostic-services.md) de memoria utilizan para su salida.

En el entorno de Windows, `afxDump` la salida del objeto `cerr` predefinido, conceptualmente similar a `OutputDebugString`la secuencia, se enruta al depurador a través de la función Windows.

La `CDumpContext` clase tiene un **<<** operador de `CObject` inserción sobrecargado ( ) para punteros que vuelcan los datos del objeto. Si necesita un formato de volcado personalizado para un objeto derivado, reemplace [CObject::Dump](../../mfc/reference/cobject-class.md#dump). La mayoría de las `Dump` clases de Microsoft Foundation implementan una función miembro invalidada.

Las clases que `CObject`no se `CString` `CTime`derivan `CTimeSpan`de , como `CDumpContext` , , y , tienen sus `CFileStatus`propios operadores de inserción sobrecargados, al igual que las estructuras de uso frecuente como , `CPoint`, y `CRect`.

Si utiliza la [IMPLEMENT_DYNAMIC](../../mfc/reference/run-time-object-model-services.md#implement_dynamic) o [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) macro en `CObject::Dump` la implementación de `CObject`la clase, imprimirá el nombre de la clase derivada. De lo contrario, se imprimirá `CObject`.

La `CDumpContext` clase está disponible con las versiones Debug `Dump` y Release de la biblioteca, pero la función miembro solo se define en la versión de depuración. Utilice **#ifdef _DEBUG**  /  `#endif` instrucciones para poner entre `Dump` corchetes el código de diagnóstico, incluidas las funciones miembro personalizadas.

Antes de crear `CDumpContext` su propio objeto, debe crear un `CFile` objeto que sirva como destino de volcado.

Para obtener `CDumpContext`más información sobre , vea [Depuración de aplicaciones MFC](/visualstudio/debugger/mfc-debugging-techniques).

**#define _DEBUG**

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CDumpContext`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="cdumpcontextcdumpcontext"></a><a name="cdumpcontext"></a>CDumpContext::CDumpContext

Construye un objeto `CDumpContext`de clase .

```
CDumpContext(CFile* pFile = NULL);
```

### <a name="parameters"></a>Parámetros

*pFile*<br/>
Puntero al `CFile` objeto que es el destino de volcado.

### <a name="remarks"></a>Observaciones

El `afxDump` objeto se construye automáticamente.

No escriba en el `CFile` subyacente mientras el contexto de volcado está activo; de lo contrario, usted interferirá con el basurero. En el entorno de Windows, la salida se `OutputDebugString`enruta al depurador a través de la función de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#12](../../mfc/codesnippet/cpp/cdumpcontext-class_1.cpp)]

## <a name="cdumpcontextdumpashex"></a><a name="dumpashex"></a>CDumpContext::DumpAsHex

Vuelca el tipo especificado con formato de números hexadecimales.

```
CDumpContext& DumpAsHex(BYTE b);
CDumpContext& DumpAsHex(DWORD dw);
CDumpContext& DumpAsHex(int n);
CDumpContext& DumpAsHex(LONG l);
CDumpContext& DumpAsHex(LONGLONG n);
CDumpContext& DumpAsHex(UINT u);
CDumpContext& DumpAsHex(ULONGLONG n);
CDumpContext& DumpAsHex(WORD w);
```

### <a name="return-value"></a>Valor devuelto

Referencia a un objeto `CDumpContext`.

### <a name="remarks"></a>Observaciones

Llame a esta función miembro para volcar el elemento del tipo especificado como un número hexadecimal. Para volcar una matriz, llame a [CDumpContext::HexDump](#hexdump).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#13](../../mfc/codesnippet/cpp/cdumpcontext-class_2.cpp)]

## <a name="cdumpcontextflush"></a><a name="flush"></a>CDumpContext::Flush

Obliga a que los datos que queden en los búferes se escriban en el archivo adjunto al contexto de volcado.

```
void Flush();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#14](../../mfc/codesnippet/cpp/cdumpcontext-class_3.cpp)]

## <a name="cdumpcontextgetdepth"></a><a name="getdepth"></a>CDumpContext::GetDepth

Determina si un volcado profundo o superficial está en proceso.

```
int GetDepth() const;
```

### <a name="return-value"></a>Valor devuelto

La profundidad del volcado `SetDepth`establecida por .

### <a name="example"></a>Ejemplo

  Consulte el ejemplo [de SetDepth](#setdepth).

## <a name="cdumpcontexthexdump"></a><a name="hexdump"></a>CDumpContext::HexDump

Vuelca una matriz de bytes con formato de números hexadecimales.

```
void HexDump(
    LPCTSTR lpszLine,
    BYTE* pby,
    int nBytes,
    int nWidth);
```

### <a name="parameters"></a>Parámetros

*lpszLine*<br/>
Una cadena para generar al principio de una nueva línea.

*Pby*<br/>
Puntero a un búfer que contiene los bytes que se van a volcar.

*nBytes*<br/>
El número de bytes que se van a volcar.

*nAncho*<br/>
Número máximo de bytes volcados por línea (no el ancho de la línea de salida).

### <a name="remarks"></a>Observaciones

Para volcar un único tipo de elemento específico como un número hexadecimal, llame a [CDumpContext::DumpAsHex](#dumpashex).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#15](../../mfc/codesnippet/cpp/cdumpcontext-class_4.cpp)]

## <a name="cdumpcontextoperator-ltlt"></a><a name="operator_lt_lt"></a>CDumpContext::operator&lt;&lt;

Produce los datos especificados en el contexto de volcado.

```
CDumpContext& operator<<(const CObject* pOb);
CDumpContext& operator<<(const CObject& ob);
CDumpContext& operator<<(LPCTSTR lpsz);
CDumpContext& operator<<(const void* lp);
CDumpContext& operator<<(BYTE by);
CDumpContext& operator<<(WORD w);
CDumpContext& operator<<(DWORD dw);
CDumpContext& operator<<(int n);
CDumpContext& operator<<(double d);
CDumpContext& operator<<(float f);
CDumpContext& operator<<(LONG l);
CDumpContext& operator<<(UINT u);
CDumpContext& operator<<(LPCWSTR lpsz);
CDumpContext& operator<<(LPCSTR lpsz);
CDumpContext& operator<<(LONGLONG n);
CDumpContext& operator<<(ULONGLONG n);
CDumpContext& operator<<(HWND h);
CDumpContext& operator<<(HDC h);
CDumpContext& operator<<(HMENU h);
CDumpContext& operator<<(HACCEL h);
CDumpContext& operator<<(HFONT h);
```

### <a name="return-value"></a>Valor devuelto

Referencia `CDumpContext`. Con el valor devuelto, puede escribir varias inserciones en una sola línea de código fuente.

### <a name="remarks"></a>Observaciones

El operador de inserción está sobrecargado para `CObject` punteros, así como para la mayoría de los tipos primitivos. Un puntero a carácter da como resultado un volcado de contenido de cadena; un puntero a **void** da como resultado un volcado hexadecimal de la dirección solamente. Un LONGLONG da como resultado un volcado de un entero de 64 bits con signo; Un ULONGLONG da como resultado un volcado de un entero sin signo de 64 bits.

Si utiliza la IMPLEMENT_DYNAMIC o IMPLEMENT_SERIAL macro en la implementación `CObject::Dump`de la clase, `CObject`el operador de inserción, a través de , imprimirá el nombre de la clase derivada. De lo contrario, se imprimirá `CObject`. Si invalida `Dump` la función de la clase, puede proporcionar una salida más significativa del contenido del objeto en lugar de un volcado hexadecimal.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#17](../../mfc/codesnippet/cpp/cdumpcontext-class_5.cpp)]

## <a name="cdumpcontextsetdepth"></a><a name="setdepth"></a>CDumpContext::SetDepth

Establece la profundidad del volcado.

```
void SetDepth(int nNewDepth);
```

### <a name="parameters"></a>Parámetros

*nNewDepth*<br/>
El nuevo valor de profundidad.

### <a name="remarks"></a>Observaciones

Si va a volcar un `CObject` tipo primitivo o simple que no contiene punteros a otros objetos, un valor de 0 es suficiente. Un valor mayor que 0 especifica un volcado profundo donde todos los objetos se vuelcan recursivamente. Por ejemplo, un volcado profundo de una colección volque todos los elementos de la colección. Puede utilizar otros valores de profundidad específicos en las clases derivadas.

> [!NOTE]
> Las referencias circulares no se detectan en volcados profundos y pueden dar lugar a bucles infinitos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#16](../../mfc/codesnippet/cpp/cdumpcontext-class_6.cpp)]

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CFile (clase)](../../mfc/reference/cfile-class.md)<br/>
[Clase CObject](../../mfc/reference/cobject-class.md)
