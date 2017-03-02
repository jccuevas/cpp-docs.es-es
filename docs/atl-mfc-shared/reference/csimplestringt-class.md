---
title: Clase CSimpleStringT | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CSimpleStringT
- ATL::CSimpleStringT
- ATL::CSimpleStringT<BaseType>
- ATL.CSimpleStringT<BaseType>
- CSimpleStringT
dev_langs:
- C++
helpviewer_keywords:
- shared classes, CSimpleStringT
- strings [C++], ATL class
- CSimpleStringT class
ms.assetid: 15814fcb-5b8f-4425-a97e-3b61fc9b48d8
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 791b9ec18cc71fe19f633c12afdc48c835c2bf14
ms.lasthandoff: 02/24/2017

---
# <a name="csimplestringt-class"></a>Clase CSimpleStringT
Esta clase representa un `CSimpleStringT` objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <typename BaseType>
class CSimpleStringT
```  
  
### <a name="parameters"></a>Parámetros  
 `BaseType`  
 El tipo de carácter de la clase string. Puede ser uno de los siguientes:  
  
- `char`(para cadenas de caracteres ANSI).  
  
- `wchar_t`(para cadenas de caracteres Unicode).  
  
- **TCHAR** (para cadenas de caracteres ANSI y Unicode).  

## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSimpleStringT::PCXSTR](#pcxstr)|Puntero a una cadena constante.|  
|[CSimpleStringT::PXSTR](#pxstr)|Un puntero a una cadena.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSimpleStringT::CSimpleStringT](#ctor)|Construye `CSimpleStringT` objetos de varias maneras.|  
|[CSimpleStringT:: ~ CSimpleStringT](#dtor)|Destructor.|  

  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSimpleStringT::Append](#append)|Anexa un `CSimpleStringT` objeto existente `CSimpleStringT` objeto.|  
|[CSimpleStringT::AppendChar](#appendchar)|Anexa un carácter existente `CSimpleStringT` objeto.|  
|[CSimpleStringT::CopyChars](#copychars)|Copia un carácter o caracteres en otra cadena.|  
|[CSimpleStringT::CopyCharsOverlapped](#copycharsoverlapped)|Copia un carácter o caracteres en otra cadena que se superponen los búferes.|  
|[CSimpleStringT::Empty](#empty)|Fuerza una cadena con una longitud de cero.|  
|[CSimpleStringT::FreeExtra](#freeextra)|Libera la memoria adicional asignada previamente por el objeto de cadena.|  
|[CSimpleStringT::GetAllocLength](#getalloclength)|Recupera la longitud de la asignación de un `CSimpleStringT` objeto.|  
|[CSimpleStringT::GetAt](#getat)|Devuelve el carácter en una posición determinada.|  
|[CSimpleStringT::GetBuffer](#getbuffer)|Devuelve un puntero a los caracteres de un `CSimpleStringT`.|  
|[CSimpleStringT::GetBufferSetLength](#getbuffersetlength)|Devuelve un puntero a los caracteres de un `CSimpleStringT`, truncado a la longitud especificada.|  
|[CSimpleStringT::GetLength](#getlength)|Devuelve el número de caracteres de un `CSimpleStringT` objeto.|  
|[CSimpleStringT::GetManager](#getmanager)|Recupera el Administrador de memoria de la `CSimpleStringT` objeto.|  
|[CSimpleStringT::GetString](#getstring)|Recupera la cadena de caracteres|  
|[CSimpleStringT::IsEmpty](#isempty)|Pruebas si un `CSimpleStringT` no contiene ningún carácter.|  
|[CSimpleStringT::LockBuffer](#lockbuffer)|Deshabilita el recuento de referencias y protege la cadena en el búfer.|  
|[CSimpleStringT::Preallocate](#preallocate)|Asigna una cantidad específica de memoria para el búfer de caracteres.|  
|[CSimpleStringT::ReleaseBuffer](#releasebuffer)|Devuelve el control del búfer devuelto por `GetBuffer`.|  
|[CSimpleStringT::ReleaseBufferSetLength](#releasebuffersetlength)|Devuelve el control del búfer devuelto por `GetBuffer`.|  
|[CSimpleStringT::SetAt](#setat)|Establece un carácter en una posición determinada.|  
|[CSimpleStringT::SetManager](#setmanager)|Establece el Administrador de memoria de un `CSimpleStringT` objeto.|  
|[CSimpleStringT::SetString](#setstring)|Establece la cadena de un `CSimpleStringT` objeto.|  
|[CSimpleStringT::StringLength](#stringlength)|Devuelve el número de caracteres de la cadena especificada.|  
|[CSimpleStringT::Truncate](#truncate)|Trunca la cadena con una longitud especificada.|  
|[CSimpleStringT::UnlockBuffer](#unlockbuffer)|Permite el recuento de referencias y libera la cadena en el búfer.|  

### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSimpleStringT::operator PCXSTR](#operator_pcxstr)|Obtiene acceso directamente a los caracteres que se almacenan en un `CSimpleStringT` objeto como una cadena de estilo C.|  
|[CSimpleStringT::operator\[\]](#operator_at)|Devuelve el carácter en una posición determinada: sustitución de operador para `GetAt`.|  
|[CSimpleStringT::operator +=](#operator_add_eq)|Concatena una nueva cadena al final de una cadena existente.|  
|[CSimpleStringT::operator =](#operator_eq)|Asigna un nuevo valor a un `CSimpleStringT` objeto.|  
  
### <a name="remarks"></a>Comentarios  
 `CSimpleStringT`es la clase base para las distintas clases de cadena admitidas por Visual C++. Proporciona la compatibilidad mínima para la administración de memoria del objeto de cadena y la manipulación del búfer básica. Para los objetos de cadena más avanzados, vea [clase CStringT](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsimpstr.h  


## <a name="a-nameappenda-csimplestringtappend"></a><a name="append"></a>CSimpleStringT::Append
Anexa un `CSimpleStringT` objeto existente `CSimpleStringT` objeto.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
void Append(const CSimpleStringT& strSrc); 
void Append(PCXSTR pszSrc, int nLength); 
void Append(PCXSTR pszSrc);
```  
#### <a name="parameters"></a>Parámetros  
 `strSrc`  
 La `CSimpleStringT` objeto se va a anexar.  
  
 `pszSrc`  
 Un puntero a una cadena que contiene los caracteres que se va a anexar.  
  
 `nLength`  
 Número de caracteres que se van a anexar.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para anexar existente `CSimpleStringT` objeto a otro `CSimpleStringT` objeto.  
  
### <a name="example"></a>Ejemplo  
 El siguiente ejemplo muestra el uso de `CSimpleStringT::Append`.  
  
```cpp  
CSimpleString str1(pMgr), str2(pMgr);
str1.SetString(_T("Soccer is"));
str2.SetString(_T(" an elegant game"));
str1.Append(str2);
ASSERT(_tcscmp(str1, _T("Soccer is an elegant game")) == 0);
```
  
##  <a name="a-nameappendchara-csimplestringtappendchar"></a><a name="appendchar"></a>CSimpleStringT::AppendChar
Anexa un carácter existente `CSimpleStringT` objeto.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
void AppendChar(XCHAR ch);
```  
#### <a name="parameters"></a>Parámetros  
 *CH*  
 El carácter que se va a anexar  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para agregar el carácter especificado al final de un miembro de `CSimpleStringT` objeto.  
  
##  <a name="a-namecopycharsa-csimplestringtcopychars"></a><a name="copychars"></a>CSimpleStringT::CopyChars  
 Copia un carácter o caracteres que un `CSimpleStringT` objeto.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
static void CopyChars(
  XCHAR* pchDest,
  const XCHAR* pchSrc, 
  int nChars) throw();
```  
#### <a name="parameters"></a>Parámetros  
 `pchDest`  
 Puntero a una cadena de caracteres.  
  
 `pchSrc`  
 Un puntero a una cadena que contiene los caracteres que se va a copiar.  
  
 `nChars`  
 El número de `pchSrc` caracteres para copiar.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para copiar los caracteres de `pchSrc` a la `pchDest` cadena.  
  
### <a name="example"></a>Ejemplo  
 El siguiente ejemplo muestra el uso de `CSimpleStringT::CopyChars`.  
  
```cpp  
CSimpleString str(_T("xxxxxxxxxxxxxxxxxxx"), 20, pMgr);
TCHAR* pszSrc = _T("Hello world!");
_tprintf_s(_T("%s\n"), str);
str.CopyChars(str.GetBuffer(), pszSrc, 12);
_tprintf_s(_T("%s\n"), str);
```
  
##  <a name="a-namecopycharsoverlappeda--csimplestringtcopycharsoverlapped"></a><a name="copycharsoverlapped"></a>CSimpleStringT::CopyCharsOverlapped
Copia un carácter o caracteres que un `CSimpleStringT` objeto.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
static void CopyCharsOverlapped(
  XCHAR* pchDest,
  const XCHAR* pchSrc,
  int nChars) throw(); 
```  
#### <a name="parameters"></a>Parámetros  
 `pchDest`  
 Puntero a una cadena de caracteres.  
  
 `pchSrc`  
 Un puntero a una cadena que contiene los caracteres que se va a copiar.  
  
 `nChars`  
 El número de `pchSrc` caracteres para copiar.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para copiar los caracteres de `pchSrc` a la `pchDest` cadena. A diferencia de `CopyChars`, `CopyCharsOverlapped` proporciona un método seguro para la copia de los búferes de caracteres que se pueden superponer.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CSimpleStringT::CopyChars](#copychars), o el código fuente de `CSimpleStringT::SetString` (ubicado en atlsimpstr.h).  
  
##  <a name="a-namectora--csimplestringtcsimplestringt"></a><a name="ctor"></a>CSimpleStringT::CSimpleStringT  
 Construye un objeto `CSimpleStringT`.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
CSimpleStringT(const XCHAR* pchSrc, int nLength, IAtlStringMgr* pStringMgr); 
CSimpleStringT(PCXSTR pszSrc, IAtlStringMgr* pStringMgr); 
CSimpleStringT(const CSimpleStringT& strSrc); 
explicit CSimpleStringT(IAtlStringMgr* pStringMgr) throw(); 
```  
#### <a name="parameters"></a>Parámetros  
 `strSrc`  
 Existente `CSimpleStringT` el objeto que se copiará en este `CSimpleStringT` objeto.  
  
 `pchSrc`  
 Un puntero a una matriz de caracteres de longitud `nLength`, no terminada en null.  
  
 `pszSrc`  
 Una cadena terminada en null que se copiará en este `CSimpleStringT` objeto.  
  
 `nLength`  
 Un recuento del número de caracteres en `pch`.  
  
 `pStringMgr`  
 Un puntero al administrador de memoria de la `CSimpleStringT` objeto. Para obtener más información acerca de `IAtlStringMgr` y administración de memoria para `CSimpleStringT`, consulte [administración de memoria y CStringT](../memory-management-with-cstringt.md).  
  
### <a name="remarks"></a>Comentarios  
 Construye un nuevo objeto `CSimpleStringT`. Dado que los constructores copian los datos de entrada en el nuevo almacenamiento asignado, pueden producir excepciones de memoria.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de `CSimpleStringT::CSimpleStringT` utilizando ATL `typedef``CSimpleString`. `CSimpleString`es una especialización de plantilla de clase utiliza `CSimpleStringT`.  
  
```cpp  
CSimpleString s1(pMgr);
// Empty string
CSimpleString s2(_T("cat"), pMgr);
// From a C string literal

CSimpleString s3(s2);
// Copy constructor
CSimpleString s4(s2 + _T(" ") + s3);

// From a string expression
CSimpleString s5(_T("xxxxxx"), 6, pMgr);
// s5 = "xxxxxx"   
```

  
##  <a name="a-nameemptya--csimplestringtempty"></a><a name="empty"></a>CSimpleStringT::Empty
Hace esto `CSimpleStringT` objeto una cadena vacía y libera memoria según corresponda.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
void Empty() throw();  
```  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [cadenas: limpieza de excepciones de CString](../cstring-exception-cleanup.md).  
  
### <a name="example"></a>Ejemplo  
 El siguiente ejemplo muestra el uso de `CSimpleStringT::Empty`.  
  
```cpp  
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());  
```  
  
##  <a name="a-namefreeextraa--csimplestringtfreeextra"></a><a name="freeextra"></a>CSimpleStringT::FreeExtra
Libera la memoria adicional asignada previamente por la cadena pero ya no es necesaria.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
void FreeExtra(); 
```  
### <a name="remarks"></a>Comentarios  
 Esto debería reducir la sobrecarga de memoria consumida por el objeto de cadena. El método reasigna el búfer a la longitud exacta devuelto por [GetLength](#getlength).  
  
### <a name="example"></a>Ejemplo  
```cpp  
CAtlString basestr;
IAtlStringMgr* pMgr;

pMgr= basestr.GetManager();
ASSERT(pMgr != NULL);

// Create a CSimpleString with 28 characters
CSimpleString str(_T("Many sports are fun to play."), 28, pMgr);
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());

// Assigning a smaller string won't cause CSimpleString to free its 
// memory, because it assumes the string will grow again anyway.
str = _T("Soccer is best!");
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());

// This call forces CSimpleString to release the extra 
// memory it doesn't need.
str.FreeExtra();
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());
```
  
### <a name="remarks"></a>Comentarios  
 El resultado de este ejemplo es la siguiente:  
  
 `Alloc length is 1031, String length is 1024`  
  
 `Alloc length is 1031, String length is 15`  
  
 `Alloc length is 15, String length is 15`  
  
##  <a name="a-namegetalloclengtha--csimplestringtgetalloclength"></a><a name="getalloclength"></a>CSimpleStringT::GetAllocLength  
Recupera la longitud de la asignación de un `CSimpleStringT` objeto.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
int GetAllocLength() const throw();  
```  
### <a name="return-value"></a>Valor devuelto  
 El número de caracteres asignado para este objeto.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para determinar el número de caracteres asignados a esta `CSimpleStringT` objeto. Consulte [FreeExtra](#freeextra) para obtener un ejemplo de una llamada a esta función.  
  
##  <a name="a-namegetata--csimplestringtgetat"></a><a name="getat"></a>CSimpleStringT::GetAt  
Devuelve un carácter de un `CSimpleStringT` objeto.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
XCHAR GetAt(int iChar) const;
```  
#### <a name="parameters"></a>Parámetros  
 `iChar`  
 Índice de base cero del carácter en el `CSimpleStringT` objeto. El `iChar` parámetro debe ser mayor o igual que 0 y menor que el valor devuelto por [GetLength](#getlength). De lo contrario, `GetAt` generará una excepción.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `XCHAR` que contiene el carácter que ocupa la posición especificada en la cadena.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para devolver el carácter especificado por `iChar`. El subíndice sobrecargado (`[]`) operador es un alias más cómodo para `GetAt`. El terminador nulo es direccionable sin generar una excepción utilizando `GetAt`. Sin embargo, no se cuentan por `GetLength`, y el valor devuelto es 0.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar `CSimpleStringT::GetAt`.  
  
```cpp  
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(s.GetAt(2) == _T('c'));
```
  
##  <a name="a-namegetbuffera--csimplestringtgetbuffer"></a><a name="getbuffer"></a>CSimpleStringT::GetBuffer  
Devuelve un puntero al búfer de caracteres interno de la `CSimpleStringT` objeto.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
PXSTR GetBuffer(int nMinBufferLength); 
PXSTR GetBuffer();
```  
#### <a name="parameters"></a>Parámetros  
 `nMinBufferLength`  
 El número mínimo de caracteres que puede contener el búfer de caracteres. Este valor no incluye el espacio de un terminador null.  
  
 Si `nMinBufferLength` es mayor que la longitud del búfer actual, `GetBuffer` destruye el búfer actual, lo reemplaza con un búfer de tamaño solicitado y restablece el recuento de referencias de objeto a cero. Si previamente ha llamado [LockBuffer](#lockbuffer) en este búfer, se pierde el bloqueo del búfer.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `PXSTR` puntero al búfer de caracteres (terminado en null) del objeto.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para devolver el contenido del búfer de la `CSimpleStringT` objeto. El valor devuelto `PXSTR` no es una constante y, por tanto, permite la modificación directa de `CSimpleStringT` contenido.  
  
 Si utiliza el puntero devuelto por `GetBuffer` para cambiar el contenido de la cadena, se debe llamar a [ReleaseBuffer](#releasebuffer) antes de utilizar cualquier otro `CSimpleStringT` métodos miembro.  
  
 La dirección devuelta por `GetBuffer` puede no ser válida después de la llamada a `ReleaseBuffer` porque adicionales `CSimpleStringT` operaciones pueden hacer que el `CSimpleStringT` búfer se reasignen. El búfer no se vuelve a asignar si no cambia la longitud de la `CSimpleStringT`.  
  
 La memoria de búfer es automáticamente libera cuando el `CSimpleStringT` se destruye el objeto.  
  
 Si realiza un seguimiento de la longitud de cadena usted mismo, no es necesario anexar el carácter nulo de terminación. Sin embargo, debe especificar la longitud de la cadena final al liberar el búfer con `ReleaseBuffer`. Si anexa un carácter null final, debe pasar –&1; (valor predeterminado) para la longitud. `ReleaseBuffer`a continuación, determina la longitud del búfer.  
  
 Si no hay memoria suficiente para satisfacer la `GetBuffer` solicitar, este método inicia una CMemoryException *.  
  
### <a name="example"></a>Ejemplo  
```cpp  
CSimpleString s(_T("abcd"), pMgr);
LPTSTR pBuffer = s.GetBuffer(10);
int sizeOfBuffer = s.GetAllocLength();

// Directly access CSimpleString buffer
_tcscpy_s(pBuffer, sizeOfBuffer, _T("Hello"));
ASSERT(_tcscmp(s, _T("Hello")) == 0);
s.ReleaseBuffer();   
```
  
##  <a name="a-namegetbuffersetlengtha--csimplestringtgetbuffersetlength"></a><a name="getbuffersetlength"></a>CSimpleStringT::GetBufferSetLength  
Devuelve un puntero al búfer de caracteres interno de la `CSimpleStringT` objeto truncar o aumenta su longitud, si es necesario para coincidir exactamente con la longitud especificada en `nLength`.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
PXSTR GetBufferSetLength(int nLength);
```  
#### <a name="parameters"></a>Parámetros  
 `nLength`  
 El tamaño exacto de la `CSimpleStringT` el búfer de caracteres en caracteres.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `PXSTR` puntero al búfer de caracteres (terminado en null) del objeto.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para recuperar una longitud especificada del búfer interno de la `CSimpleStringT` objeto. El valor devuelto `PXSTR` puntero no es `const` y, por tanto, permite la modificación directa de `CSimpleStringT` contenido.  
  
 Si utiliza el puntero devuelto por [GetBufferSetLength](#getbuffersetlength) para cambiar el contenido de la cadena, llame a `ReleaseBuffer` para actualizar el estado interno de `CsimpleStringT` antes de utilizar cualquier otro `CSimpleStringT` métodos.  
  
 La dirección devuelta por `GetBufferSetLength` puede no ser válida después de la llamada a `ReleaseBuffer` porque adicionales `CSimpleStringT` operaciones pueden hacer que el `CSimpleStringT` búfer se reasignen. El búfer no se vuelve a asignar si no cambia la longitud de la `CSimpleStringT`.  
  
 La memoria de búfer es automáticamente libera cuando el `CSimpleStringT` se destruye el objeto.  
  
 Si realiza un seguimiento de la longitud de cadena usted mismo, no no anexar el carácter nulo de terminación. Debe especificar la longitud de la cadena final al liberar el búfer mediante `ReleaseBuffer`. Si anexa un carácter nulo al llamar a `ReleaseBuffer`, pasar –&1; (valor predeterminado) para que la longitud del `ReleaseBuffer`, y `ReleaseBuffer` llevará a cabo una `strlen` en el búfer para determinar su longitud.  
  
 Para obtener más información acerca de recuento de referencias, consulte los artículos siguientes:  
  
- [Administrar la duración de objetos mediante el recuento de referencias](http://msdn.microsoft.com/library/windows/desktop/ms687260) del SDK de Windows. 
  
- [Implementación de recuento de referencias](http://msdn.microsoft.com/library/windows/desktop/ms693431) del SDK de Windows.
  
- [Reglas de administración de recuentos de referencias](http://msdn.microsoft.com/library/windows/desktop/ms692481) del SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 El siguiente ejemplo muestra el uso de `CSimpleStringT::GetBufferSetLength`.  
  
```cpp  
CSimpleString str(pMgr);
LPTSTR pstr = str.GetBufferSetLength(3);
pstr[0] = _T('C');
pstr[1] = _T('u');
pstr[2] = _T('p');

// No need for trailing zero or call to ReleaseBuffer() 
// because GetBufferSetLength() set it for us.

str += _T(" soccer is best!");
ASSERT(_tcscmp(str, _T("Cup soccer is best!")) == 0);
```
  
##  <a name="a-namegetlengtha--csimplestringtgetlength"></a><a name="getlength"></a>CSimpleStringT::GetLength  
Devuelve el número de caracteres de la `CSimpleStringT` objeto.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
int GetLength() const throw();  
```  
### <a name="return-value"></a>Valor devuelto  
 Un recuento de los caracteres de la cadena.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para devolver el número de caracteres en el objeto. El recuento no incluye un terminador null.  
  
 Para juegos de caracteres multibyte (MBCS) `GetLength` recuentos de cada byte de 8 bits de caracteres; es decir, una inicial y final de un carácter multibyte se cuentan como dos bytes. Consulte [FreeExtra](#freeextra) para obtener un ejemplo de una llamada a esta función.  
  
##  <a name="a-namegetmanagera--csimplestringtgetmanager"></a><a name="getmanager"></a>CSimpleStringT::GetManager  
Recupera el Administrador de memoria de la `CSimpleStringT` objeto.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
IAtlStringMgr* GetManager() const throw();  
```  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al administrador de memoria para el `CSimpleStringT` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para recuperar la memoria utilizado por el administrador del `CSimpleStringT` objeto. Para obtener más información acerca de los administradores de memoria y objetos de cadena, vea [administración de memoria y CStringT](../memory-management-with-cstringt.md).  
  
##  <a name="a-namegetstringa--csimplestringtgetstring"></a><a name="getstring"></a>CSimpleStringT::GetString
Recupera la cadena de caracteres.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
PCXSTR GetString() const throw();
```  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una cadena de caracteres terminada en null.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para recuperar la cadena de caracteres asociada a la `CSimpleStringT` objeto.  
  
> [!NOTE]
>  El valor devuelto `PCXSTR` puntero es `const` y no permite la modificación directa de `CSimpleStringT` contenido.  
  
### <a name="example"></a>Ejemplo  
 El siguiente ejemplo muestra el uso de `CSimpleStringT::GetString`.  
  
```cpp  
CSimpleString str(pMgr);
str += _T("Cup soccer is best!");
_tprintf_s(_T("%s"), str.GetString());
```
  
##  <a name="a-nameisemptya--csimplestringtisempty"></a><a name="isempty"></a>CSimpleStringT::IsEmpty  
Pruebas de un `CSimpleStringT` objeto para la condición vacía.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
bool IsEmpty() const throw();  
```  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si la `CSimpleStringT` objeto tiene longitud 0; en caso contrario **false**.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para determinar si el objeto contiene una cadena vacía.  
  
### <a name="example"></a>Ejemplo  
 El siguiente ejemplo muestra el uso de `CSimpleStringT::IsEmpty`.  
  
```cpp  
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```
  
##  <a name="a-namelockbuffera--csimplestringtlockbuffer"></a><a name="lockbuffer"></a>CSimpleStringT::LockBuffer  
Deshabilita el recuento de referencias y protege la cadena en el búfer.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
PXSTR LockBuffer();
```  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CSimpleStringT` objeto o una cadena terminada en null.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para bloquear el búfer de la `CSimpleStringT` objeto. Llamando a `LockBuffer`, se crea una copia de la cadena con -1 para el recuento de referencias. Cuando el valor de recuento de referencia es -1, se considera que la cadena en el búfer está en estado "bloqueado". Mientras se encuentra en un estado bloqueado, la protección de la cadena de dos maneras:  
  
-   Ninguna otra cadena puede obtener una referencia a los datos en la cadena bloqueada, incluso si esa cadena se asigna a la cadena bloqueada.  
  
-   La cadena bloqueada nunca hará referencia a otra cadena, incluso si esa cadena otra se copia en la cadena bloqueada.  
  
 Bloquea la cadena en el búfer, se asegura de que la suspensión exclusivo de la cadena en el búfer se mantendrán intacto.  
  
 Cuando haya terminado con `LockBuffer`, llame a [UnlockBuffer](#unlockbuffer) para restablecer el recuento de referencias a 1.  
  
> [!NOTE]
>  Si se llama a [GetBuffer](#getbuffer) en un búfer bloqueado y establecer el `GetBuffer` parámetro `nMinBufferLength` a mayor que la longitud del búfer actual, perderá el bloqueo del búfer. Esta llamada a `GetBuffer` destruye el búfer actual, lo reemplaza con un búfer de tamaño solicitado y restablece el recuento de referencias en cero.  
  
 Para obtener más información acerca de recuento de referencias, consulte los artículos siguientes:  
  
- [Administrar la duración de objetos mediante el recuento de referencias](http://msdn.microsoft.com/library/windows/desktop/ms687260) del SDK de Windows  
  
- [Implementación de recuento de referencias](http://msdn.microsoft.com/library/windows/desktop/ms693431) del SDK de Windows  
  
- [Reglas de administración de recuentos de referencias](http://msdn.microsoft.com/library/windows/desktop/ms692481) del SDK de Windows  
  
### <a name="example"></a>Ejemplo  
 El siguiente ejemplo muestra el uso de `CSimpleStringT::LockBuffer`.  
  
```cpp  
CSimpleString str(_T("Hello"), pMgr);
TCHAR ch;

str.LockBuffer();
ch = str.GetAt(2);
_tprintf_s(_T("%c"), ch);
str.UnlockBuffer();
```
  
##  <a name="a-nameoperatorata--csimplestringtoperator"></a><a name="operator_at"></a>CSimpleStringT::operator\[\]  
Llame a esta función para obtener acceso a un solo carácter de la matriz de caracteres.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
XCHAR operator[](int iChar) const;
```  
#### <a name="parameters"></a>Parámetros  
 `iChar`  
 Índice de base cero de un carácter en la cadena.  
  
### <a name="remarks"></a>Comentarios  
 El subíndice sobrecargado (`[]`) operador devuelve un único carácter especificado por el índice de base cero en `iChar`. Este operador es un sustituto adecuado para la [GetAt](#getat) función miembro.  
  
> [!NOTE]
>  Puede utilizar el subíndice (`[]`) (operador) para obtener el valor de un carácter en un `CSimpleStringT`, pero no se puede usar para cambiar el valor de un carácter en un `CSimpleStringT`.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de **[] CSimpleStringT::operator**.  
  
```cpp  
CSimpleString s(_T("abc"), pMgr);
ASSERT(s[1] == _T('b'));
```
  
## <a name="a-nameoperatorata--csimplestringtoperator-"></a><a name="operator_at"></a>CSimpleStringT::operator\[\]
Llame a esta función para obtener acceso a un solo carácter de la matriz de caracteres.  
  
### <a name="syntax"></a>Sintaxis  
  
```   
XCHAR operator[](int iChar) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `iChar`  
 Índice de base cero de un carácter en la cadena.  
  
### <a name="remarks"></a>Comentarios  
 El subíndice sobrecargado (`[]`) operador devuelve un único carácter especificado por el índice de base cero en `iChar`. Este operador es un sustituto adecuado para la [GetAt](#getat) función miembro.  
  
> [!NOTE]
>  Puede utilizar el subíndice (`[]`) (operador) para obtener el valor de un carácter en un `CSimpleStringT`, pero no se puede usar para cambiar el valor de un carácter en un `CSimpleStringT`.  
  
  
##  <a name="a-nameoperatoraddeqa--csimplestringtoperator-"></a><a name="operator_add_eq"></a>CSimpleStringT::operator +=  
Combina una nueva cadena o un carácter al final de una cadena existente.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
CSimpleStringT& operator +=(PCXSTR pszSrc); 
CSimpleStringT& operator +=(const CSimpleStringT& strSrc); 
template<int t_nSize>  
CSimpleStringT& operator+=(const CStaticString< XCHAR, t_nSize >& strSrc); 
CSimpleStringT& operator +=(char ch); 
CSimpleStringT& operator +=(unsigned char ch); 
CSimpleStringT& operator +=(wchar_t ch);
```  
#### <a name="parameters"></a>Parámetros  
 `pszSrc`  
 Un puntero a una cadena terminada en null.  
  
 `strSrc`  
 Un puntero a un `CSimpleStringT` objeto.  
  
 *CH*  
 Carácter que se va a anexar.  
  
### <a name="remarks"></a>Comentarios  
 El operador acepta otro `CSimpleStringT` objeto o un carácter. Tenga en cuenta que la memoria se pueden producir excepciones cada vez que utilice este operador de concatenación, como se puede asignar el nuevo almacenamiento para los caracteres que se agregan a la `CSimpleStringT` objeto.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de **CSimpleStringT::operator +=**.  
  
```cpp  
CSimpleString str(_T("abc"), pMgr);
ASSERT(_tcscmp((str += _T("def")), _T("abcdef")) == 0);
```
  
##  <a name="a-nameoperatoreqa--csimplestringtoperator-"></a><a name="operator_eq"></a>CSimpleStringT::operator =  
Asigna un nuevo valor a un `CSimpleStringT` objeto.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
CSimpleStringT& operator =(PCXSTR pszSrc); 
CSimpleStringT& operator =(const CSimpleStringT& strSrc);
```  
#### <a name="parameters"></a>Parámetros  
 `pszSrc`  
 Un puntero a una cadena terminada en null.  
  
 `strSrc`  
 Un puntero a un `CSimpleStringT` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Si la cadena de destino (el lado izquierdo) ya es lo suficientemente grande como para almacenar los nuevos datos, no se realiza ninguna nueva asignación de memoria. Tenga en cuenta que la memoria se pueden producir excepciones cuando se utiliza el operador de asignación porque a menudo se asigna nuevo almacenamiento para contener resultante `CSimpleStringT` objeto.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de **CSimpleStringT::operator =**.  
  
```cpp  
CSimpleString s1(pMgr), s2(pMgr);
// Empty CSimpleStringT objects

s1 = _T("cat");
// s1 = "cat"
ASSERT(_tcscmp(s1, _T("cat")) == 0);

s2 = s1;               // s1 and s2 each = "cat"
ASSERT(_tcscmp(s2, _T("cat")) == 0);

s1 = _T("the ") + s1;      
// Or expressions
ASSERT(_tcscmp(s1, _T("the cat")) == 0);

s1 = _T("x");
// Or just individual characters
ASSERT(_tcscmp(s1, _T("x")) == 0);
```
  
##  <a name="a-nameoperatorpcxstra--csimplestringtoperator-pcxstr"></a><a name="operator_pcxstr"></a>CSimpleStringT::operator PCXSTR  

 Obtiene acceso directamente a los caracteres que se almacenan en un `CSimpleStringT` objeto como una cadena de estilo C.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
operator PCXSTR() const throw();
```  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a los datos de la cadena de carácter.  
  
### <a name="remarks"></a>Comentarios  
 No se copian caracteres; se devuelve sólo un puntero. Tenga cuidado con este operador. Si cambia un `CString` objeto tras haber obtenido el puntero de carácter, puede provocar la reasignación de memoria que invalida el puntero.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de **CSimpleStringT::operator PCXSTR**.  
  
```cpp  
// If the prototype of a function is known to the compiler, 
// the PCXSTR cast operator may be invoked implicitly.

CSimpleString strSports(L"Soccer is Best!", pMgr);
WCHAR sz[1024];

wcscpy_s(sz, strSports);

// If the prototype isn't known or is a va_arg prototype, 
// you must invoke the cast operator explicitly. For example, 
// the va_arg part of a call to swprintf_s() needs the cast:

swprintf_s(sz, 1024, L"I think that %s!\n", (PCWSTR)strSports);

// While the format parameter is known to be an PCXSTR and 
// therefore doesn't need the cast:

swprintf_s(sz, 1024, strSports);

// Note that some situations are ambiguous. This line will 
// put the address of the strSports object to stdout:

wcout << strSports;

// while this line will put the content of the string out:

wcout << (PCWSTR)strSports;   
``` 
  
##  <a name="a-namepcxstra--csimplestringtpcxstr"></a><a name="pcxstr"></a>CSimpleStringT::PCXSTR
Puntero a una cadena constante.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef ChTraitsBase< BaseType >::PCXSTR PCXSTR;    
```  
##  <a name="a-namepreallocatea--csimplestringtpreallocate"></a><a name="preallocate"></a>CSimpleStringT::Preallocate  
Asigna una cantidad específica de bytes para la `CSimpleStringT` objeto.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
void Preallocate( int nLength);
```  
#### <a name="parameters"></a>Parámetros  
 `nLength`  
 El tamaño exacto de la `CSimpleStringT` el búfer de caracteres en caracteres.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para asignar un tamaño de búfer específico para el `CSimpleStringT` objeto.  
  
 `CSimpleStringT`genera un `STATUS_NO_MEMORY` excepción si no se puede asignar espacio para el búfer de caracteres. De forma predeterminada, se realiza la asignación de memoria mediante funciones de la API de WIN32 `HeapAlloc` o `HeapReAlloc`.  
  
### <a name="example"></a>Ejemplo  
 El siguiente ejemplo muestra el uso de `CSimpleStringT::Preallocate`.  
  
```cpp  
CSimpleString str(pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
str.Preallocate(100);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
```
  
##  <a name="a-namepxstra--csimplestringtpxstr"></a><a name="pxstr"></a>CSimpleStringT::PXSTR  
Un puntero a una cadena.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef ChTraitsBase< BaseType >::PXSTR PXSTR;  
```  
##  <a name="a-namereleasebuffera--csimplestringtreleasebuffer"></a><a name="releasebuffer"></a>CSimpleStringT::ReleaseBuffer  
Devuelve el control del búfer asignado por [GetBuffer](#getbuffer).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
void ReleaseBuffer(int nNewLength = -1);
```  
#### <a name="parameters"></a>Parámetros  
 `nNewLength`  
 La nueva longitud de la cadena de caracteres, sin contar un terminador null. Si la cadena es nula termina, se establece el valor predeterminado de-1 la `CSimpleStringT` tamaño a la longitud actual de la cadena.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para reasignar o liberar el búfer del objeto de cadena. Si sabe que la cadena en el búfer termina en null, se puede omitir el `nNewLength` argumento. Si la cadena no es nula terminada, use `nNewLength` para especificar su longitud. La dirección devuelta por [GetBuffer](#getbuffer) no es válida después de la llamada a `ReleaseBuffer` o cualquier otro `CSimpleStringT` operación.  
  
### <a name="example"></a>Ejemplo  
 El siguiente ejemplo muestra el uso de `CSimpleStringT::ReleaseBuffer`.  
  
```cpp  
const int bufferSize = 1024;
CSimpleString s(_T("abc"), pMgr);
LPTSTR p = s.GetBuffer(bufferSize);
_tcscpy_s(p, bufferSize, _T("abc"));

  // use the buffer directly
ASSERT(s.GetLength() == 3);

// String length = 3
s.ReleaseBuffer();

// Surplus memory released, p is now invalid.
ASSERT(s.GetLength() == 3);

// Length still 3
```
  
##  <a name="a-namereleasebuffersetlengtha--csimplestringtreleasebuffersetlength"></a><a name="releasebuffersetlength"></a>CSimpleStringT::ReleaseBufferSetLength

Devuelve el control del búfer asignado por [GetBuffer](#getbuffer).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
void ReleaseBufferSetLength(int nNewLength);
```  
#### <a name="parameters"></a>Parámetros  
 `nNewLength`  
 La longitud de la cadena que se libera  
  
### <a name="remarks"></a>Comentarios  
 Esta función es funcionalmente similar a [ReleaseBuffer](#releasebuffer) excepto en que se debe pasar una longitud válida para el objeto de cadena.  
  
##  <a name="a-namesetata--csimplestringtsetat"></a><a name="setat"></a>CSimpleStringT::SetAt  
Establece un solo carácter de un `CSimpleStringT` objeto.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
void SetAt(int iChar, XCHAR ch);
```  
#### <a name="parameters"></a>Parámetros  
 `iChar`  
 Índice de base cero del carácter en el `CSimpleStringT` objeto. El `iChar` parámetro debe ser mayor o igual que 0 y menor que el valor devuelto por [GetLength](#getlength).  
  
 *CH*  
 El carácter de nueva.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para sobrescribir el carácter situado en `iChar`. Este método no ampliará la cadena si `iChar` supera los límites de la cadena existente.  
  
### <a name="example"></a>Ejemplo  
 El siguiente ejemplo muestra el uso de `CSimpleStringT::SetAt`.  
  
```cpp  
CSimpleString s(_T("abcdef"), pMgr);
s.SetAt(1, _T('a'));
ASSERT(_tcscmp(s, _T("aacdef")) == 0);
``` 
  
##  <a name="a-namesetmanagera--csimplestringtsetmanager"></a><a name="setmanager"></a>CSimpleStringT::SetManager  
Especifica el Administrador de memoria de la `CSimpleStringT` objeto.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
void SetManager(IAtlStringMgr* pStringMgr);
```  
#### <a name="parameters"></a>Parámetros  
 `pStringMgr`  
 Un puntero al nuevo administrador de memoria.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para especificar una nueva memoria utilizado por el administrador del `CSimpleStringT` objeto. Para obtener más información acerca de los administradores de memoria y objetos de cadena, vea [administración de memoria y CStringT](../memory-management-with-cstringt.md).  
  
### <a name="example"></a>Ejemplo  
 El siguiente ejemplo muestra el uso de `CSimpleStringT::SetManager`.  
  
```cpp  
CSimpleString s(pMgr);
s.SetManager(pCustomMgr);
```
  
##  <a name="a-namesetstringa--csimplestringtsetstring"></a><a name="setstring"></a>CSimpleStringT::SetString  
Establece la cadena de un `CSimpleStringT` objeto.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
void SetString(PCXSTR pszSrc, int nLength); 
void SetString(PCXSTR pszSrc);
```  
#### <a name="parameters"></a>Parámetros  
 `pszSrc`  
 Un puntero a una cadena terminada en null.  
  
 `nLength`  
 Un recuento del número de caracteres en `pszSrc`.  
  
### <a name="remarks"></a>Comentarios  
 Copiar una cadena en el `CSimpleStringT` objeto. `SetString`sobrescribe los datos más antiguos de la cadena en el búfer.  
  
 Ambas versiones de `SetString` comprobar si `pszSrc` es un puntero nulo y si lo está, se produce un **E_INVALIDARG** error.  
  
 La versión de un parámetro de `SetString` espera `pszSrc` para que apunte a una cadena terminada en null.  
  
 La versión de dos parámetros de `SetString` también espera que `pszSrc` una cadena terminada en null. Usa `nLength` como la longitud de cadena a menos que se encuentra en primer lugar un terminador null.  
  
 La versión de dos parámetros de `SetString` también comprueba si `pszSrc` señala a una ubicación en el búfer actual en `CSimpleStringT`. En este caso especial, `SetString` usa una función de copia de memoria que no sobrescribe los datos de cadena como copia los datos de cadena a su búfer.  
  
### <a name="example"></a>Ejemplo  
 El siguiente ejemplo muestra el uso de `CSimpleStringT::SetString`.  
  
```cpp  
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(_tcscmp(s, _T("abcdef")) == 0);
s.SetString(_T("Soccer"), 6);
ASSERT(_tcscmp(s, _T("Soccer")) == 0);
```
  
##  <a name="a-namestringlengtha--csimplestringtstringlength"></a><a name="stringlength"></a>CSimpleStringT::StringLength  
Devuelve el número de caracteres de la cadena especificada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
ATL_NOINLINE static int StringLength(PCXSTR psz) throw();
```  
#### <a name="parameters"></a>Parámetros  
 `psz`  
 Un puntero a una cadena terminada en null.  
  
### <a name="return-value"></a>Valor devuelto  
 El número de caracteres de `psz`; sin contar un terminador null.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para recuperar el número de caracteres de la cadena señalada por `psz`.  
  
### <a name="example"></a>Ejemplo  
 El siguiente ejemplo muestra el uso de `CSimpleStringT::StringLength`.  
  
```cpp  
ASSERT(CSimpleString::StringLength(_T("soccer")) == 6);
``` 
  
##  <a name="a-nametruncatea--csimplestringttruncate"></a><a name="truncate"></a>CSimpleStringT::Truncate
Trunca la cadena a la nueva longitud.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
void Truncate(int nNewLength);
```  
#### <a name="parameters"></a>Parámetros  
 `nNewLength`  
 La nueva longitud de la cadena.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para truncar el contenido de la cadena a la nueva longitud.  
  
> [!NOTE]
>  Esto no afecta a la longitud del búfer asignada. Para aumentar o disminuir el búfer actual, consulte [FreeExtra](#freeextra) y [Preallocate](#preallocate).  
  
### <a name="example"></a>Ejemplo  
 El siguiente ejemplo muestra el uso de `CSimpleStringT::Truncate`.  
  
```cpp  
CSimpleString str(_T("abcdefghi"), pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetLength());
_tprintf_s(_T("Contents: %s\n"), str);
str.Truncate(4);
_tprintf_s(_T("Allocated length: %d\n"), str.GetLength());
_tprintf_s(_T("Contents: %s\n"), str);
``` 
  
##  <a name="a-nameunlockbuffera--csimplestringtunlockbuffer"></a><a name="unlockbuffer"></a>CSimpleStringT::UnlockBuffer
 Desbloquea el búfer de la `CSimpleStringT` objeto.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
void UnlockBuffer() throw();
```  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para restablecer el recuento de referencias de la cadena a 1.  
  
 El `CSimpleStringT` destructor llama automáticamente a `UnlockBuffer` para asegurarse de que el búfer no está bloqueado cuando se llama al destructor. Para obtener un ejemplo de este método, consulte [LockBuffer](#lockbuffer).  
  
##  <a name="a-namedtora--csimplestringtcsimplestringt"></a><a name="dtor"></a>CSimpleStringT:: ~ CSimpleStringT
Destruye un objeto `CSimpleStringT`.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
~CSimpleStringT() throw();
```  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para destruir la `CSimpleStringT` objeto.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases compartidas de ATL y MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
