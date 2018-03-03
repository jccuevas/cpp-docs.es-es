---
title: Clase CComVariant | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComVariant
- ATLCOMCLI/ATL::CComVariant
- ATLCOMCLI/ATL::CComVariant::CComVariant
- ATLCOMCLI/ATL::CComVariant::Attach
- ATLCOMCLI/ATL::CComVariant::ChangeType
- ATLCOMCLI/ATL::CComVariant::Clear
- ATLCOMCLI/ATL::CComVariant::Copy
- ATLCOMCLI/ATL::CComVariant::CopyTo
- ATLCOMCLI/ATL::CComVariant::Detach
- ATLCOMCLI/ATL::CComVariant::GetSize
- ATLCOMCLI/ATL::CComVariant::ReadFromStream
- ATLCOMCLI/ATL::CComVariant::SetByRef
- ATLCOMCLI/ATL::CComVariant::WriteToStream
dev_langs:
- C++
helpviewer_keywords:
- VARIANT macro
- CComVariant class
- VARIANT macro, ATL
ms.assetid: 4d31149c-d005-44b5-a509-10f84afa2b61
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 67e5aeee2aaa96b143962beb0790e3854ff7de01
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ccomvariant-class"></a>Clase CComVariant
Esta clase se ajusta a la `VARIANT` tipo, proporcionando un miembro que indica el tipo de datos almacenados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
cpp
class CComVariant : public tagVARIANT  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComVariant::CComVariant](#ccomvariant)|El constructor.|  
|[CComVariant:: ~ CComVariant](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComVariant::Attach](#attach)|Asocia un **VARIANT** a la `CComVariant` objeto.|  
|[CComVariant::ChangeType](#changetype)|Convierte el `CComVariant` objeto a un nuevo tipo.|  
|[CComVariant::Clear](#clear)|Borra la `CComVariant` objeto.|  
|[CComVariant::Copy](#copy)|Copia un **VARIANT** a la `CComVariant` objeto.|  
|[CComVariant::CopyTo](#copyto)|Copia el contenido de la `CComVariant` objeto.|  
|[CComVariant::Detach](#detach)|Desasocia subyacente **VARIANT** desde el `CComVariant` objeto.|  
|[CComVariant::GetSize](#getsize)|Devuelve el tamaño en número de bytes del contenido de la `CComVariant` objeto.|  
|[CComVariant::ReadFromStream](#readfromstream)|Carga un **VARIANT** desde una secuencia.|  
|[CComVariant::SetByRef](#setbyref)|Inicializa el `CComVariant` objeto y establece el **vt** miembro **VT_BYREF**.|  
|[CComVariant:: WriteToStream](#writetostream)|Guarda subyacente **VARIANT** en una secuencia.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|||  
|-|-|  
|[CComVariant::operator <](#operator_lt)|Indica si la `CComVariant` objeto es menor que el especificado **VARIANT**.|  
|[CComVariant::operator >](#operator_gt)|Indica si la `CComVariant` objeto es mayor que el especificado **VARIANT**.|  
|[operador! =](#operator_neq)|Indica si la `CComVariant` objeto no es igual a la especificada **VARIANT**.|  
|[operador =](#operator_eq)|Asigna un valor a la `CComVariant` objeto.|  
|[operador ==](#operator_eq_eq)|Indica si la `CComVariant` objeto es igual a la especificada **VARIANT**.|  
  
## <a name="remarks"></a>Comentarios  
 `CComVariant`ajusta el `VARIANT and VARIANTARG` tipo, que consta de una unión y un miembro que indica el tipo de los datos almacenados en la unión. **VARIANT**normalmente se utilizan en la automatización.  
  
 `CComVariant`se deriva de la **VARIANT** escriba por lo que puede ser utilizado, donde un **VARIANT** puede utilizarse. Por ejemplo, puede usar el **V_VT** macro para extraer el tipo de un `CComVariant` o puede tener acceso a la **vt** miembro directamente al igual que lo haría con un **VARIANT**.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `tagVARIANT`  
  
 `CComVariant`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcomcli.h  
  
##  <a name="attach"></a>CComVariant::Attach  
 Borra de forma segura el contenido actual de la `CComVariant` de objetos, copia el contenido de `pSrc` en este objeto, a continuación, Establece el tipo variant de `pSrc` a `VT_EMPTY`.  
  
```
HRESULT Attach(VARIANT* pSrc);
```  
  
### <a name="parameters"></a>Parámetros  
 `pSrc`  
 [in] Apunta a la [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) para adjuntarlo al objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Propiedad de los datos mantenidos por `pSrc` se transfiere a la `CComVariant` objeto.  
  
##  <a name="ccomvariant"></a>CComVariant::CComVariant  
 Cada constructor controla la inicialización seguro para la ejecución de la `CComVariant` objeto mediante una llamada a la `VariantInit` función de Win32 o estableciendo el valor del objeto y el tipo según los parámetros pasados.  
  
```
CComVariant() throw();
CComVariant(const CComVariant& varSrc);
CComVariant(const VARIANT& varSrc);
CComVariant(LPCOLESTR lpszSrc);
CComVariant(LPCSTR lpszSrc);
CComVariant(bool bSrc);
CComVariant(BYTE nSrc) throw();
CComVariant(int nSrc, VARTYPE vtSrc = VT_I4) throw();
CComVariant(unsigned int  nSrc, VARTYPE vtSrc = VT_UI4) throw();
CComVariant(shor  nSrc) throw();
CComVariant(unsigned short nSrc) throw();
CComVariant(long  nSrc, VARTYPE vtSrc = VT_I4) throw();
CComVariant(unsigned long  nSrc) throw();
CComVariant(LONGLONG  nSrc) throw();
CComVariant(ULONGLONG  nSrc) throw();
CComVariant(float  fltSrc) throw();
CComVariant(double  dblSrc, VARTYPE vtSrc = VT_R8) throw();
CComVariant(CY  cySrc) throw();
CComVariant(IDispatch* pSrc) throw();
CComVariant(IUnknown* pSrc) throw();
CComVariant(const SAFEARRAY* pSrc);
CComVariant(char  cSrc) throw();
CComVariant(const CComBSTR& bstrSrc);
```  
  
### <a name="parameters"></a>Parámetros  
 *varSrc*  
 [in] El `CComVariant` o `VARIANT` utilizado para inicializar el `CComVariant` objeto. El contenido de la variante de origen se copia en el destino sin realizar ninguna conversión.  
  
 `lpszSrc`  
 [in] La cadena de caracteres que se usa para inicializar la `CComVariant` objeto. Puede pasar una cero anchos (Unicode) cadena de caracteres terminada en el **LPCOLESTR** versión del constructor, o una cadena ANSI para la `LPCSTR` versión. En cualquier caso, la cadena se convierte en Unicode `BSTR` asignados mediante **SysAllocString**. El tipo de la `CComVariant` objeto será `VT_BSTR`.  
  
 `bSrc`  
 [in] El `bool` utilizado para inicializar el `CComVariant` objeto. El `bool` argumento se convierte en una **VARIANT_BOOL** antes de que se almacena. El tipo de la `CComVariant` objeto será `VT_BOOL`.  
  
 `nSrc`  
 [in] El `int`, **bytes**, **corto**, **largo**, **LONGLONG**, **ULONGLONG**, **entero corto sin signo**, `unsigned long`, o `unsigned int` utilizado para inicializar el `CComVariant` objeto. El tipo de la `CComVariant` objeto será `VT_I4`, `VT_UI1`, `VT_I2`, `VT_I4`, **VT_I8**, **VT_UI8**, **VT_UI2**,  **VT_UI4**, o **VT_UI4**, respectivamente.  
  
 `vtSrc`  
 [in] El tipo de la variante. Cuando el primer parámetro es `int`, los tipos válidos son `VT_I4` y **VT_INT**. Cuando el primer parámetro es **largo**, los tipos válidos son `VT_I4` y `VT_ERROR`. Cuando el primer parámetro es **doble**, los tipos válidos son `VT_R8` y `VT_DATE`. Cuando el primer parámetro es `unsigned int`, los tipos válidos son **VT_UI4** y **VT_UINT**.  
  
 `fltSrc`  
 [in] El **float** utilizado para inicializar el `CComVariant` objeto. El tipo de la `CComVariant` objeto será `VT_R4`.  
  
 `dblSrc`  
 [in] El **doble** utilizado para inicializar el `CComVariant` objeto. El tipo de la `CComVariant` objeto será `VT_R8`.  
  
 `cySrc`  
 [in] El **CY** utilizado para inicializar el `CComVariant` objeto. El tipo de la `CComVariant` objeto será `VT_CY`.  
  
 `pSrc`  
 [in] El `IDispatch` o **IUnknown** puntero que se utiliza para inicializar la `CComVariant` objeto. `AddRef`se llamará en el puntero de interfaz. El tipo de la `CComVariant` objeto será **VT_DISPATCH** o **VT_UNKNOWN**, respectivamente.  
  
 O bien, el **SAFERRAY** puntero que se utiliza para inicializar la `CComVariant` objeto. Una copia de la **SAFEARRAY** se almacena en la `CComVariant` objeto. El tipo de la `CComVariant` objeto será una combinación del tipo original de la **SAFEARRAY** y **VT_ARRAY**.  
  
 `cSrc`  
 [in] El `char` utilizado para inicializar el `CComVariant` objeto. El tipo de la `CComVariant` objeto será **VT_I1**.  
  
 `bstrSrc`  
 [in] El BSTR se utiliza para inicializar la `CComVariant` objeto. El tipo de la `CComVariant` objeto será `VT_BSTR`.  
  
### <a name="remarks"></a>Comentarios  
 El destructor administra limpieza mediante una llamada a [CComVariant::Clear](#clear).  
  
##  <a name="dtor"></a>CComVariant:: ~ CComVariant  
 Destructor.  
  
```
~CComVariant() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método administra la limpieza mediante una llamada a [CComVariant::Clear](#clear).  
  
##  <a name="changetype"></a>CComVariant::ChangeType  
 Convierte el `CComVariant` objeto a un nuevo tipo.  
  
```
HRESULT ChangeType(VARTYPE vtNew, const VARIANT* pSrc = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `vtNew`  
 [in] El nuevo tipo para el `CComVariant` objeto.  
  
 `pSrc`  
 [in] Un puntero a la `VARIANT` cuyo valor se convertirá en el nuevo tipo. El valor predeterminado es **NULL**, lo que significa que la `CComVariant` objeto se convertirá en su lugar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Si se pasa un valor para `pSrc`, `ChangeType` usará **VARIANT** como origen para la conversión. En caso contrario, la `CComVariant` objeto será el origen.  
  
##  <a name="clear"></a>CComVariant::Clear  
 Borra la `CComVariant` objeto mediante una llamada a la `VariantClear` función de Win32.  
  
```
HRESULT Clear();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 El destructor llama automáticamente a **desactive**.  
  
##  <a name="copy"></a>CComVariant::Copy  
 Libera la `CComVariant` objeto y, a continuación, le asigna una copia del elemento especificado **VARIANT**.  
  
```
HRESULT Copy(const VARIANT* pSrc);
```  
  
### <a name="parameters"></a>Parámetros  
 `pSrc`  
 [in] Un puntero a la [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) va a copiar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
##  <a name="copyto"></a>CComVariant::CopyTo  
 Copia el contenido de la `CComVariant` objeto.  
  
```
HRESULT CopyTo(BSTR* pstrDest);
```  
  
### <a name="parameters"></a>Parámetros  
 *pstrDest*  
 Apunta a un `BSTR` que recibirán una copia del contenido de la `CComVariant` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 El **CComVariant** objeto debe ser del tipo `VT_BSTR`.  
  
##  <a name="detach"></a>CComVariant::Detach  
 Desasocia subyacente **VARIANT** desde el `CComVariant` objeto y establece el tipo del objeto en `VT_EMPTY`.  
  
```
HRESULT Detach(VARIANT* pDest);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDest`  
 [out] Devuelve subyacente `VARIANT` valor del objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que el contenido de la `VARIANT` referenciado por `pDest` se borrará automáticamente antes de que se asigna el valor y el tipo de la llamada a **CComVariant** objeto.  
  
##  <a name="getsize"></a>CComVariant::GetSize  
 De tamaño fijo simple `VARIANT`, este método devuelve el `sizeof` el tipo de datos subyacente más `sizeof(VARTYPE)`.  
  
```
ULONG GetSize() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño en bytes del contenido actual de la `CComVariant` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Si el `VARIANT` contiene un puntero de interfaz, `GetSize` consulta `IPersistStream` o `IPersistStreamInit`. Si tiene éxito, el valor devuelto es los 32 bits de orden inferior del valor devuelto por `GetSizeMax` además de la interfaz `sizeof` una `CLSID` y `sizeof(VARTYPE)`. Si el puntero de interfaz es `NULL`, `GetSize` devuelve el `sizeof` una `CLSID` más `sizeof(VARTYPE)`. Si es mayor que el tamaño total `ULONG_MAX`, `GetSize` devuelve `sizeof(VARTYPE)` que indica un error.  
  
 En todos los demás casos, un archivo temporal `VARIANT` de tipo `VT_BSTR` se convierte en el actual `VARIANT`. La longitud de este `BSTR` se calcula como el tamaño de la longitud de la cadena y la longitud de la propia cadena más el tamaño del carácter nulo más `sizeof(VARTYPE)`. Si el `VARIANT` no se puede convertir a un `VARIANT` de tipo `VT_BSTR`, `GetSize` devuelve `sizeof(VARTYPE)`.  
  
 El tamaño devuelto por este método coincide con el número de bytes usados por [CComVariant:: WriteToStream](#writetostream) en condiciones correcta.  
  
##  <a name="operator_eq"></a>CComVariant::operator =  
 Asigna un valor y el tipo correspondiente a la `CComVariant` objeto.  
  
```
CComVariant& operator=(const CComVariant& varSrc);
CComVariant& operator=(const VARIANT& varSrc);
CComVariant& operator=(const CComBSTR& bstrSrc);
CComVariant& operator=(LPCOLESTR lpszSrc);
CComVariant& operator=(LPCSTR lpszSrc);
CComVariant& operator=(bool bSrc);
CComVariant& operator=(BYTE nSrc) throw();
CComVariant& operator=int nSrc) throw();
CComVariant& operator=(unsigned int nSrc) throw();
CComVariant& operator=(short nSrc) throw();
CComVariant& operator=(unsigned short nSrc) throw();
CComVariant& operator=(long nSrc) throw();
CComVariant& operator=(unsigned long nSrc) throw();
CComVariant& operator=(LONGLONG nSrc) throw();
CComVariant& operator=(ULONGLONG nSrc) throw();
CComVariant& operator=(float fltSrc) throw();
CComVariant& operator=(double dblSrc) throw();
CComVariant& operator=(CY cySrc) throw();
CComVariant& operator=(IDispatch* pSrc) throw();
CComVariant& operator=(IUnknown* pSrc) throw();
CComVariant& operator=(const SAFEARRAY* pSrc);
CComVariant& operator=(char cSrc) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *varSrc*  
 [in] El `CComVariant` o [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) que se asignará a la `CComVariant` objeto. El contenido de la variante de origen se copia en el destino sin realizar ninguna conversión.  
  
 `bstrSrc`  
 [in] El BSTR que se asignará a la `CComVariant` objeto. El tipo de la `CComVariant` objeto será `VT_BSTR`.  
  
 `lpszSrc`  
 [in] La cadena de caracteres que se asignará a la `CComVariant` objeto. Puede pasar una cero anchos (Unicode) cadena de caracteres terminada en el **LPCOLESTR** versión del operador o una cadena ANSI para la `LPCSTR` versión. En cualquier caso, la cadena se convierte en Unicode `BSTR` asignados mediante **SysAllocString**. El tipo de la `CComVariant` objeto será `VT_BSTR`.  
  
 `bSrc`  
 [in] El `bool` que se asignará a la `CComVariant` objeto. El `bool` argumento se convierte en una **VARIANT_BOOL** antes de que se almacena. El tipo de la `CComVariant` objeto será `VT_BOOL`.  
  
 `nSrc`  
 [in] El `int`, **bytes**, **corto**, **largo**, **LONGLONG**, **ULONGLONG**, **entero corto sin signo**, `unsigned long`, o `unsigned int` que se asignará a la `CComVariant` objeto. El tipo de la `CComVariant` objeto será `VT_I4`, `VT_UI1`, `VT_I2`, `VT_I4`, **VT_I8**, **VT_UI8**, **VT_UI2**,  **VT_UI4**, o **VT_UI4**, respectivamente.  
  
 `fltSrc`  
 [in] El **float** que se asignará a la `CComVariant` objeto. El tipo de la `CComVariant` objeto será `VT_R4`.  
  
 `dblSrc`  
 [in] El **doble** que se asignará a la `CComVariant` objeto. El tipo de la `CComVariant` objeto será `VT_R8`.  
  
 `cySrc`  
 [in] El **CY** que se asignará a la `CComVariant` objeto. El tipo de la `CComVariant` objeto será `VT_CY`.  
  
 `pSrc`  
 [in] El `IDispatch` o **IUnknown** puntero que se asignará a la `CComVariant` objeto. `AddRef`se llamará en el puntero de interfaz. El tipo de la `CComVariant` objeto será **VT_DISPATCH** o **VT_UNKNOWN**, respectivamente.  
  
 O, una **SAFEARRAY** puntero que se asignará a la `CComVariant` objeto. Una copia de la **SAFEARRAY** se almacena en la `CComVariant` objeto. El tipo de la `CComVariant` objeto será una combinación del tipo original de la **SAFEARRAY** y **VT_ARRAY**.  
  
 `cSrc`  
 [in] El carácter que se asignará a la `CComVariant` objeto. El tipo de la `CComVariant` objeto será **VT_I1**.  
  
##  <a name="operator_eq_eq"></a>CComVariant::operator ==  
 Indica si la `CComVariant` objeto es igual a la especificada **VARIANT**.  
  
```
bool operator==(const VARIANT& varSrc) const throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Devuelve **true** si el valor y tipo de *varSrc* son iguales que el valor y tipo, respectivamente, de la `CComVariant` objeto. en caso contrario, **false**. El operador utiliza el idioma del usuario predeterminado para realizar la comparación.  
  
 El operador compara únicamente el valor de los tipos variantes. Compara cadenas, enteros y puntos flotantes, pero no las matrices o registros.  
  
##  <a name="operator_neq"></a>CComVariant::operator! =  
 Indica si la `CComVariant` objeto no es igual a la especificada **VARIANT**.  
  
```
bool operator!=(const VARIANT& varSrc) const throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Devuelve **true** si el valor o el tipo de *varSrc* no es igual al valor o tipo, respectivamente, de la `CComVariant` objeto. en caso contrario, **false**. El operador utiliza el idioma del usuario predeterminado para realizar la comparación.  
  
 El operador compara únicamente el valor de los tipos variantes. Compara cadenas, enteros y puntos flotantes, pero no las matrices o registros.  
  
##  <a name="operator_lt"></a>CComVariant::operator&lt;  
 Indica si la `CComVariant` objeto es menor que el especificado **VARIANT**.  
  
```
bool operator<(const VARIANT& varSrc) const throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Devuelve **true** si el valor de la `CComVariant` objeto es menor que el valor de *varSrc*. en caso contrario, **false**. El operador utiliza el idioma del usuario predeterminado para realizar la comparación.  
  
##  <a name="operator_gt"></a>CComVariant::operator&gt;  
 Indica si la `CComVariant` objeto es mayor que el especificado **VARIANT**.  
  
```
bool operator>(const VARIANT& varSrc) const throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Devuelve **true** si el valor de la `CComVariant` objeto es mayor que el valor de *varSrc*. en caso contrario, **false**. El operador utiliza el idioma del usuario predeterminado para realizar la comparación.  
  
##  <a name="readfromstream"></a>CComVariant::ReadFromStream  
 Establece subyacente **VARIANT** a la **VARIANT** contenidos en la secuencia especificada.  
  
```
HRESULT ReadFromStream(IStream* pStream);
```  
  
### <a name="parameters"></a>Parámetros  
 `pStream`  
 [in] Un puntero a la [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) interfaz en la secuencia que contiene los datos.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 **ReadToStream** requiere una llamada anterior a [WriteToStream](#writetostream).  
  
##  <a name="setbyref"></a>CComVariant::SetByRef  
 Inicializa el `CComVariant` objeto y establece el **vt** miembro **VT_BYREF**.  
  
```
template < typename T >
void SetByRef(T* pT) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de **VARIANT**, por ejemplo, `BSTR`, `int`, o `char`.  
  
 *pT*  
 El puntero que se utiliza para inicializar la `CComVariant` objeto.  
  
### <a name="remarks"></a>Comentarios  
 `SetByRef`es una plantilla de función que inicializa el `CComVariant` objeto al puntero *pT* y establece la **vt** miembro **VT_BYREF**. Por ejemplo:  
  
 [!code-cpp[NVC_ATL_Utilities#76](../../atl/codesnippet/cpp/ccomvariant-class_1.cpp)]  
  
##  <a name="writetostream"></a>CComVariant:: WriteToStream  
 Guarda subyacente **VARIANT** en una secuencia.  
  
```
HRESULT WriteToStream(IStream* pStream);
```  
  
### <a name="parameters"></a>Parámetros  
 `pStream`  
 [in] Un puntero a la [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) interfaz en una secuencia.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)