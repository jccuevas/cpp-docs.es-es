---
title: CDumpContext (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDumpContext
- AFX/CDumpContext
- AFX/CDumpContext::CDumpContext
- AFX/CDumpContext::DumpAsHex
- AFX/CDumpContext::Flush
- AFX/CDumpContext::GetDepth
- AFX/CDumpContext::HexDump
- AFX/CDumpContext::SetDepth
dev_langs:
- C++
helpviewer_keywords:
- CDumpContext [MFC], CDumpContext
- CDumpContext [MFC], DumpAsHex
- CDumpContext [MFC], Flush
- CDumpContext [MFC], GetDepth
- CDumpContext [MFC], HexDump
- CDumpContext [MFC], SetDepth
ms.assetid: 98c52b2d-14b5-48ed-b423-479a4d1c60fa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 332b67d5eb4bcd3bb6c3d47fa5692a7b3ef81531
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410408"
---
# <a name="cdumpcontext-class"></a>CDumpContext (clase)

Admite resultados de diagnóstico orientados a secuencia en forma de texto legible.

## <a name="syntax"></a>Sintaxis

```
class CDumpContext
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CDumpContext::CDumpContext](#cdumpcontext)|Construye un objeto `CDumpContext`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CDumpContext::DumpAsHex](#dumpashex)|Vuelca el elemento indicado en formato hexadecimal.|
|[CDumpContext::Flush](#flush)|Vacía los datos en el búfer de contexto de volcado de memoria.|
|[CDumpContext::GetDepth](#getdepth)|Obtiene un entero que corresponde a la profundidad del volcado de memoria.|
|[CDumpContext::HexDump](#hexdump)|Los volcados de bytes que contiene una matriz en formato hexadecimal.|
|[CDumpContext::SetDepth](#setdepth)|Establece la profundidad del volcado de memoria.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CDumpContext::operator &lt;&lt;](#operator_lt_lt)|Inserta las variables y objetos en el contexto de volcado de memoria.|

## <a name="remarks"></a>Comentarios

`CDumpContext` no tiene una clase base.

Puede usar [afxDump](diagnostic-services.md#afxdump), un predeclarados `CDumpContext` objeto para la mayor parte de su proceso de volcado. La `afxDump` objeto solo está disponible en la versión de depuración de la biblioteca Microsoft Foundation Class.

Varios de la memoria [servicios de diagnóstico](../../mfc/reference/diagnostic-services.md) usar `afxDump` para su salida.

En el entorno de Windows, la salida de predefinido `afxDump` objeto, conceptualmente similar a la `cerr` de flujo, se enruta al depurador mediante la función de Windows `OutputDebugString`.

El `CDumpContext` clase tiene una inserción sobrecargada ( **<<**) operador para `CObject` punteros que vuelque los datos del objeto. Si tiene un formato de volcado de memoria personalizado para un objeto derivado, invalidar [CObject::Dump](../../mfc/reference/cobject-class.md#dump). Implementa un invalidado la mayoría de las clases de Microsoft Foundation `Dump` función miembro.

Las clases que no se derivan `CObject`, tales como `CString`, `CTime`, y `CTimeSpan`, tienen sus propios sobrecargado `CDumpContext` operadores de inserción, como estructuras utilizadas con frecuencia, como `CFileStatus`, `CPoint`, y `CRect`.

Si usas el [IMPLEMENT_DYNAMIC](../../mfc/reference/run-time-object-model-services.md#implement_dynamic) o [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) macro en la implementación de la clase, a continuación, `CObject::Dump` imprimirá el nombre de su `CObject`-clase derivada. En caso contrario, imprimirá `CObject`.

El `CDumpContext` clase está disponible con las versiones de depuración y lanzamiento de la biblioteca, pero la `Dump` función miembro solo se define en la versión de depuración. Use **#ifdef _DEBUG**  /  `#endif` instrucciones para poner entre corchetes del código de diagnóstico, incluidas personalizado `Dump` funciones miembro.

Antes de crear su propio `CDumpContext` objeto, debe crear un `CFile` objeto que actúa como el destino de volcado de memoria.

Para obtener más información sobre `CDumpContext`, consulte [depurar aplicaciones de MFC](/visualstudio/debugger/mfc-debugging-techniques).

**#define _DEBUG**

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CDumpContext`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="cdumpcontext"></a>  CDumpContext::CDumpContext

Crea un objeto de clase `CDumpContext`.

```
CDumpContext(CFile* pFile = NULL);
```

### <a name="parameters"></a>Parámetros

*pFile*<br/>
Un puntero a la `CFile` objeto que constituye el destino de volcado de memoria.

### <a name="remarks"></a>Comentarios

La `afxDump` objeto se crea automáticamente.

No escriba subyacente `CFile` mientras el contexto de volcado de memoria está activo; en caso contrario, ya que interferiría con la información del volcado. En el entorno de Windows, se enruta la salida al depurador mediante la función de Windows `OutputDebugString`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#12](../../mfc/codesnippet/cpp/cdumpcontext-class_1.cpp)]

##  <a name="dumpashex"></a>  CDumpContext::DumpAsHex

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

### <a name="remarks"></a>Comentarios

Llame a esta función miembro para el elemento del tipo especificado como un número hexadecimal de volcado de memoria. Para volcar una matriz, llame a [CDumpContext::HexDump](#hexdump).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#13](../../mfc/codesnippet/cpp/cdumpcontext-class_2.cpp)]

##  <a name="flush"></a>  CDumpContext::Flush

Obliga a los datos que quedan en los búferes se escriban en el archivo adjunto en el contexto de volcado.

```
void Flush();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#14](../../mfc/codesnippet/cpp/cdumpcontext-class_3.cpp)]

##  <a name="getdepth"></a>  CDumpContext::GetDepth

Determina si un volcado profundo o superficial está en proceso.

```
int GetDepth() const;
```

### <a name="return-value"></a>Valor devuelto

La profundidad del volcado de memoria según lo establecido por `SetDepth`.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [SetDepth](#setdepth).

##  <a name="hexdump"></a>  CDumpContext::HexDump

Volcados de memoria de una matriz de bytes con formato de números hexadecimales.

```
void HexDump(
    LPCTSTR lpszLine,
    BYTE* pby,
    int nBytes,
    int nWidth);
```

### <a name="parameters"></a>Parámetros

*lpszLine*<br/>
Una cadena en la salida del principio de una nueva línea.

*pby*<br/>
Un puntero a un búfer que contiene los bytes que se va a volcar.

*nBytes*<br/>
El número de bytes para volcar.

*nWidth*<br/>
Vuelca el número máximo de bytes por línea (no el ancho de la línea de salida).

### <a name="remarks"></a>Comentarios

Para volcar un tipo de elemento único y específico como un número hexadecimal, llame a [CDumpContext::DumpAsHex](#dumpashex).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#15](../../mfc/codesnippet/cpp/cdumpcontext-class_4.cpp)]

##  <a name="operator_lt_lt"></a>  CDumpContext::operator &lt;&lt;

Genera los datos especificados en el contexto de volcado.

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

Un `CDumpContext` referencia. El valor devuelto puede escribir varias inserciones en una sola línea de código fuente.

### <a name="remarks"></a>Comentarios

Se sobrecarga el operador de inserción para `CObject` punteros, así como para los tipos más primitivos. Un puntero al carácter da como resultado un volcado del contenido de cadena; un puntero a **void** da como resultado un volcado hexadecimal de la dirección solo. Un LONGLONG da como resultado un volcado de memoria de un entero con signo de 64 bits; ULONGLONG da como resultado un volcado de memoria de un entero de 64 bits sin signo.

Si usa la macro IMPLEMENT_DYNAMIC o IMPLEMENT_SERIAL en la implementación de la clase y, a continuación, el operador de inserción a través de `CObject::Dump`, imprimirá el nombre de su `CObject`-clase derivada. En caso contrario, imprimirá `CObject`. Si invalida el `Dump` función de la clase, a continuación, puede proporcionar una salida más significativa de contenido del objeto en lugar de un volcado hexadecimal.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#17](../../mfc/codesnippet/cpp/cdumpcontext-class_5.cpp)]

##  <a name="setdepth"></a>  CDumpContext::SetDepth

Establece la profundidad para el volcado de memoria.

```
void SetDepth(int nNewDepth);
```

### <a name="parameters"></a>Parámetros

*nNewDepth*<br/>
El nuevo valor de profundidad.

### <a name="remarks"></a>Comentarios

Si el volcado de un tipo primitivo o simple `CObject` que no contiene punteros a otros objetos, a continuación, basta con un valor de 0. Un valor mayor que 0 especifica un volcado de memoria detallado donde todos los objetos están volcadas de forma recursiva. Por ejemplo, un volcado de profundidad de una colección volcará todos los elementos de la colección. Puede usar otros valores específicos de profundidad en sus clases derivadas.

> [!NOTE]
>  Las referencias circulares no se detectan en profundidad volcados de memoria y pueden dar lugar a bucles infinitos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#16](../../mfc/codesnippet/cpp/cdumpcontext-class_6.cpp)]

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CFile (clase)](../../mfc/reference/cfile-class.md)<br/>
[CObject (clase)](../../mfc/reference/cobject-class.md)
