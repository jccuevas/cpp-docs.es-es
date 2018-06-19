---
title: Clase COleVariant | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleVariant
- AFXDISP/COleVariant
- AFXDISP/COleVariant::COleVariant
- AFXDISP/COleVariant::Attach
- AFXDISP/COleVariant::ChangeType
- AFXDISP/COleVariant::Clear
- AFXDISP/COleVariant::Detach
- AFXDISP/COleVariant::GetByteArrayFromVariantArray
- AFXDISP/COleVariant::SetString
dev_langs:
- C++
helpviewer_keywords:
- COleVariant [MFC], COleVariant
- COleVariant [MFC], Attach
- COleVariant [MFC], ChangeType
- COleVariant [MFC], Clear
- COleVariant [MFC], Detach
- COleVariant [MFC], GetByteArrayFromVariantArray
- COleVariant [MFC], SetString
ms.assetid: e1b5cd4a-b066-4b9b-b48b-6215ed52d998
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6b7f0da1f53bf2c6b0e216195be37746eab9abd1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33378526"
---
# <a name="colevariant-class"></a>COleVariant (clase)
Encapsula el tipo de datos [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) .  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleVariant : public tagVARIANT  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleVariant::COleVariant](#colevariant)|Construye un objeto `COleVariant`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleVariant::Attach](#attach)|Asocia un **VARIANT** a una `COleVariant`.|  
|[COleVariant::ChangeType](#changetype)|Cambia el tipo de variante de `COleVariant` objeto.|  
|[COleVariant::Clear](#clear)|Borra este `COleVariant` objeto.|  
|[COleVariant::Detach](#detach)|Desasocia un **VARIANT** desde una `COleVariant` y devuelve el **VARIANT**.|  
|[COleVariant::GetByteArrayFromVariantArray](#getbytearrayfromvariantarray)|Recupera una matriz de bytes de una matriz de variant existente.|  
|[COleVariant::SetString](#setstring)|Establece la cadena a un tipo determinado, normalmente ANSI.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleVariant::operator LPCVARIANT](#operator_lpcvariant)|Convierte un `COleVariant` valor en un `LPCVARIANT`.|  
|[COleVariant::operator LPVARIANT](#operator_lpvariant)|Convierte un `COleVariant` objeto en un `LPVARIANT`.|  
|[COleVariant::operator =](#operator_eq)|Copia un `COleVariant` valor.|  
|[COleVariant::operator ==](#operator_eq_eq)|Compara dos `COleVariant` valores.|  
|[COleVariant::operator &lt; &lt;, &gt;&gt;](#operator_lt_lt__gt_gt)|Salidas un `COleVariant` valor a `CArchive` o `CDumpContext` y escribe un `COleVariant` objeto `CArchive`.|  
  
## <a name="remarks"></a>Comentarios  
 Este tipo de datos se usa en la automatización OLE. En concreto, el [DISPPARAMS](http://msdn.microsoft.com/en-us/a16e5a21-766e-4287-b039-13429aa78f8b) estructura contiene un puntero a una matriz de **VARIANT** estructuras. A **DISPPARAMS** estructura se utiliza para pasar parámetros a [IDispatch:: Invoke](http://msdn.microsoft.com/en-us/964ade8e-9d8a-4d32-bd47-aa678912a54d).  
  
> [!NOTE]
>  Esta clase se deriva de la **VARIANT** estructura. Esto significa que puede pasar un `COleVariant` en un parámetro que requiere un **VARIANT** y que los miembros de datos de la **VARIANT** estructura son miembros de datos accesibles de `COleVariant`.  
  
 Los dos relacionados con las clases MFC [COleCurrency](../../mfc/reference/colecurrency-class.md) y [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) encapsular los tipos de datos variant **moneda** ( `VT_CY`) y **fecha** ( `VT_DATE`). El `COleVariant` clase se utiliza habitualmente en las clases DAO, consulte estas clases para un uso típico de esta clase, por ejemplo [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) y [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).  
  
 Para obtener más información, consulte el [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118), [moneda](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e), [DISPPARAMS](http://msdn.microsoft.com/en-us/a16e5a21-766e-4287-b039-13429aa78f8b), y [IDispatch:: Invoke](http://msdn.microsoft.com/en-us/964ade8e-9d8a-4d32-bd47-aa678912a54d) entradas en el SDK de Windows.  
  
 Para obtener más información sobre la `COleVariant` clase y su uso en la automatización OLE, vea "Pasar parámetros de automatización OLE" en el artículo [automatización](../../mfc/automation.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `tagVARIANT`  
  
 `COleVariant`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdisp.h  
  
##  <a name="attach"></a>  COleVariant::Attach  
 Llame a esta función para adjuntar el determinado [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) objeto al actual `COleVariant` objeto.  
  
```  
void Attach(VARIANT& varSrc);
```  
  
### <a name="parameters"></a>Parámetros  
 *varSrc*  
 Existente **VARIANT** objeto para adjuntarlo a la corriente `COleVariant` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Esta función establece el [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4) de *varSrc* a `VT_EMPTY`.  
  
 Para obtener más información, consulte el [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) y [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4) entradas en el SDK de Windows.  
  
##  <a name="colevariant"></a>  COleVariant::COleVariant  
 Construye un objeto `COleVariant`.  
  
```  
COleVariant(); 
COleVariant(const VARIANT& varSrc); 
COleVariant(const COleVariant& varSrc); 
COleVariant(LPCVARIANT pSrc); 
COleVariant(LPCTSTR lpszSrc); 
COleVariant(LPCTSTR lpszSrc, VARTYPE vtSrc); 
COleVariant(CString& strSrc); 
COleVariant(BYTE nSrc); 
COleVariant(short nSrc, VARTYPE vtSrc = VT_I2); 
COleVariant(long lSrc,VARTYPE vtSrc = VT_I4); 
COleVariant(const COleCurrency& curSrc); 
COleVariant(float fltSrc); 
COleVariant(double dblSrc); 
COleVariant(const COleDateTime& timeSrc); 
COleVariant(const CByteArray& arrSrc); 
COleVariant(const CLongBinary& lbSrc); 
COleVariant(LPCITEMIDLIST pidl);
```  
  
### <a name="parameters"></a>Parámetros  
 *varSrc*  
 Existente `COleVariant` o **VARIANT** objeto que se copiará en el nuevo `COleVariant` objeto.  
  
 `pSrc`  
 Un puntero a un **VARIANT** objeto que se copiará en el nuevo `COleVariant` objeto.  
  
 `lpszSrc`  
 Una cadena terminada en null que se copiará en el nuevo `COleVariant` objeto.  
  
 `vtSrc`  
 El `VARTYPE` para el nuevo `COleVariant` objeto.  
  
 `strSrc`  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que se copiará en el nuevo `COleVariant` objeto.  
  
 `nSrc`, `lSrc`  
 Un valor numérico que se va a copiar en el nuevo objeto `COleVariant`.  
  
 `vtSrc`  
 El `VARTYPE` para el nuevo `COleVariant` objeto.  
  
 `curSrc`  
 A [COleCurrency](../../mfc/reference/colecurrency-class.md) objeto que se copiará en el nuevo `COleVariant` objeto.  
  
 `fltSrc`, `dblSrc`  
 Un valor numérico que se va a copiar en el nuevo objeto `COleVariant`.  
  
 `timeSrc`  
 A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que se copiará en el nuevo `COleVariant` objeto.  
  
 `arrSrc`  
 A [CByteArray](../../mfc/reference/cbytearray-class.md) objeto que se copiará en el nuevo `COleVariant` objeto.  
  
 `lbSrc`  
 A [CLongBinary](../../mfc/reference/clongbinary-class.md) objeto que se copiará en el nuevo `COleVariant` objeto.  
  
 `pidl`  
 Un puntero a un [ITEMIDLIST](http://msdn.microsoft.com/library/windows/desktop/bb773321) estructura que se copiará en el nuevo `COleVariant` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Todos estos constructores crean nuevos `COleVariant` objetos inicializados en el valor especificado. A continuación se muestra una breve descripción de cada uno de estos constructores.  
  
- **() COleVariant** crea vacío `COleVariant` objeto, `VT_EMPTY`.  
  
- **COleVariant (** *varSrc* **)** copia existente **VARIANT** o `COleVariant` objeto. El tipo variant se conserva.  
  
- **COleVariant (** `pSrc` **)** copia existente **VARIANT** o `COleVariant` objeto. El tipo variant se conserva.  
  
- **COleVariant (** `lpszSrc` **)** copia una cadena en el nuevo objeto, `VT_BSTR` (UNICODE).  
  
- **COleVariant (** `lpszSrc` **,** `vtSrc` **)** copia una cadena en el nuevo objeto. El parámetro `vtSrc` debe ser `VT_BSTR` (UNICODE) o `VT_BSTRT` (ANSI).  
  
- **COleVariant (** `strSrc` **)** copia una cadena en el nuevo objeto, **VT_BSTR** (UNICODE).  
  
- **COleVariant (** `nSrc` **)** copia un entero de 8 bits en el nuevo objeto, `VT_UI1`.  
  
- **COleVariant (** `nSrc` **,** `vtSrc` **)** copia un entero de 16 bits (o valor booleano) en el nuevo objeto. El parámetro `vtSrc` debe ser `VT_I2` o `VT_BOOL`.  
  
- **COleVariant (** `lSrc` **,** `vtSrc` **)** copia un entero de 32 bits (o `SCODE` valor) en el nuevo objeto. El parámetro `vtSrc` debe ser `VT_I4`, `VT_ERROR`, o `VT_BOOL`.  
  
- **COleVariant (** `curSrc` **)** copias un **COleCurrency** valor en el nuevo objeto, `VT_CY`.  
  
- **COleVariant (** `fltSrc` **)** copia un valor de punto flotante de 32 bits en el nuevo objeto, `VT_R4`.  
  
- **COleVariant (** `dblSrc` **)** copia un valor de punto flotante de 64 bits en el nuevo objeto, `VT_R8`.  
  
- **COleVariant (** `timeSrc` **)** copias un `COleDateTime` valor en el nuevo objeto, `VT_DATE`.  
  
- **COleVariant (** `arrSrc` **)** copias un `CByteArray` objeto en el nuevo objeto, `VT_EMPTY`.  
  
- **COleVariant (** `lbSrc` **)** copias un `CLongBinary` objeto en el nuevo objeto, `VT_EMPTY`.  
  
 Para obtener más información sobre `SCODE`, consulte [estructura de códigos de Error COM](http://msdn.microsoft.com/library/windows/desktop/ms690088) del SDK de Windows.  
  
##  <a name="changetype"></a>  COleVariant::ChangeType  
 Convierte el tipo de valor de tipo variant en este `COleVariant` objeto.  
  
```  
void ChangeType(VARTYPE vartype, LPVARIANT pSrc = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `vartype`  
 El [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4) para este `COleVariant` objeto.  
  
 `pSrc`  
 Un puntero a la [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) objeto que se va a convertir. Si este valor es **NULL**, este `COleVariant` objeto se usa como origen para la conversión.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte el [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118), [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4), y [VariantChangeType](http://msdn.microsoft.com/en-us/48a51e32-95d7-4eeb-8106-f5043ffa2fd1) entradas en el SDK de Windows.  
  
##  <a name="clear"></a>  COleVariant::Clear  
 Borra la **VARIANT**.  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>Comentarios  
 Esto establece la **VARTYPE** para este objeto en `VT_EMPTY`. El `COleVariant` destructor llama a esta función.  
  
 Para obtener más información, consulte el `VARIANT`, `VARTYPE`, y `VariantClear` entradas en el SDK de Windows.  
  
##  <a name="detach"></a>  COleVariant::Detach  
 Desasocia subyacente [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) objeto desde este `COleVariant` objeto.  
  
```  
VARIANT Detach();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función establece el [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4) para este `COleVariant` el objeto a `VT_EMPTY`.  
  
> [!NOTE]
>  Después de llamar a **separar**, es responsabilidad del llamador para llamar a **VariantClear** en resultante **VARIANT** estructura.  
  
 Para obtener más información, consulte el [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118), [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4), y [VariantClear](http://msdn.microsoft.com/en-us/28741d81-8404-4f85-95d3-5c209ec13835) entradas en el SDK de Windows.  
  
##  <a name="getbytearrayfromvariantarray"></a>  COleVariant::GetByteArrayFromVariantArray  
 Recupera una matriz de bytes de una matriz de variant existente  
  
```  
void GetByteArrayFromVariantArray(CByteArray& bytes);
```  
  
### <a name="parameters"></a>Parámetros  
 `bytes`  
 Una referencia a un archivo [CByteArray](../../mfc/reference/cbytearray-class.md) objeto.  
  
##  <a name="operator_lpcvariant"></a>  COleVariant::operator LPCVARIANT  
 Este operador de conversión devuelve un `VARIANT` estructura cuyo valor se copia desde este `COleVariant` objeto.  
  
```  
operator LPCVARIANT() const; 
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="operator_lpvariant"></a>  COleVariant::operator LPVARIANT  
 Llame a este operador de conversión para tener acceso a subyacente `VARIANT` estructura para este `COleVariant` objeto.  
  
```  
operator LPVARIANT();
```   
  
### <a name="remarks"></a>Comentarios  
  
> [!CAUTION]
>  Cambie el valor en el **VARIANT** estructura tiene acceso por el puntero devuelto por esta función cambiará el valor de esta `COleVariant` objeto.  
  
##  <a name="operator_eq"></a>  COleVariant::operator =  
 Estos operadores de asignaciones sobrecargados copie el valor de origen en este `COleVariant` objeto.  
  
```  
const COleVariant& operator=(const VARIANT& varSrc); 
const COleVariant& operator=(LPCVARIANT pSrc); 
const COleVariant& operator=(const COleVariant& varSrc); 
const COleVariant& operator=(const LPCTSTR lpszSrc);
const COleVariant& operator=(const CString& strSrc); 
const COleVariant& operator=(BYTE nSrc); 
const COleVariant& operator=(short nSrc); 
const COleVariant& operator=(long lSrc); 
const COleVariant& operator=(const COleCurrency& curSrc); 
const COleVariant& operator=(float fltSrc); 
const COleVariant& operator=(double dblSrc); 
const COleVariant& operator=(const COleDateTime& dateSrc); 
const COleVariant& operator=(const CByteArray& arrSrc); 
const COleVariant& operator=(const CLongBinary& lbSrc);
```  
  
### <a name="remarks"></a>Comentarios  
 A continuación se ofrece una breve descripción de cada operador:  
  
- **operador = (** *varSrc ***)** copia existente **VARIANT** o `COleVariant` objeto en este objeto.  
  
- **operador = (** `pSrc` **)** copias la **VARIANT** objeto acceso `pSrc` en este objeto.  
  
- **operador = (** `lpszSrc` **)** copia una cadena terminada en null en este objeto y establece el **VARTYPE** a `VT_BSTR`.  
  
- **operador = (** `strSrc` **)** copias un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto en este objeto y los conjuntos de la **VARTYPE** a `VT_BSTR`.  
  
- **operador = (** `nSrc` **)** copia un valor del entero de 8 bits o de 16 bits en este objeto. Si `nSrc` es un valor de 8 bits, la **VARTYPE** de esto se establece en `VT_UI1`. Si `nSrc` es un valor de 16 bits y la **VARTYPE** de esto es `VT_BOOL`, mantiene; de lo contrario, se establece en `VT_I2`.  
  
- **operador = (** `lSrc` **)** copia un valor entero de 32 bits en este objeto. Si el **VARTYPE** de esto es `VT_ERROR`, mantiene; de lo contrario, se establece en `VT_I4`.  
  
- **operador = (** `curSrc` **)** copias un [COleCurrency](../../mfc/reference/colecurrency-class.md) objeto en este objeto y los conjuntos de la **VARTYPE** a `VT_CY`.  
  
- **operador = (** `fltSrc` **)** copia un valor de punto flotante de 32 bits en este objeto y establece el **VARTYPE** a `VT_R4`.  
  
- **operador = (** `dblSrc` **)** copia un valor de punto flotante de 64 bits en este objeto y establece el **VARTYPE** a `VT_R8`.  
  
- **operador = (** `dateSrc` **)** copias un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto en este objeto y los conjuntos de la **VARTYPE** a `VT_DATE`.  
  
- **operador = (** `arrSrc` **)** copias un [CByteArray](../../mfc/reference/cbytearray-class.md) objeto en esta `COleVariant` objeto.  
  
- **operador = (** `lbSrc` **)** copias un [CLongBinary](../../mfc/reference/clongbinary-class.md) objeto en esta `COleVariant` objeto.  
  
 Para obtener más información, consulte el [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) y [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4) entradas en el SDK de Windows.  
  
##  <a name="operator_eq_eq"></a>  COleVariant::operator ==  
 Este operador compara dos valores de tipo variantes y devuelve un valor distinto de cero si son iguales; en caso contrario es 0.  
  
```  
BOOL operator==(const VARIANT& varSrc) const; 
BOOL operator==(LPCVARIANT pSrc) const;
```  
  
##  <a name="operator_lt_lt__gt_gt"></a>  COleVariant::operator &lt; &lt;, &gt;&gt;  
 Salidas un `COleVariant` valor a `CArchive` o **CdumpContext** y escribe un `COleVariant` objeto `CArchive`.  
  
```  
friend CDumpContext& AFXAPI operator<<(
    CDumpContext& dc,  
    OleVariant varSrc);
 
friend CArchive& AFXAPI operator<<(
    CArchive& ar,  
    COleVariant varSrc);
 
friend CArchive& AFXAPI operator>>(
    CArchive& ar,  
    COleVariant& varSrc);
```  
  
### <a name="remarks"></a>Comentarios  
 El `COleVariant` inserción ( **< \<**) admite el operador diagnóstico volcado y almacenar en un archivo. La extracción ( **>>**) operador admite la carga de un archivo.  
  
##  <a name="setstring"></a>  COleVariant::SetString  
 Establece la cadena a un tipo determinado.  
  
```  
void SetString(LPCTSTR lpszSrc, VARTYPE vtSrc);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszSrc`  
 Una cadena terminada en null que se copiará en el nuevo `COleVariant` objeto.  
  
 *VtSrc*  
 El **VARTYPE** para el nuevo `COleVariant` objeto.  
  
### <a name="remarks"></a>Comentarios  
 El parámetro `vtSrc` debe ser `VT_BSTR` (UNICODE) o `VT_BSTRT` (ANSI). `SetString` Normalmente se usa para establecer las cadenas a ANSI, desde el valor predeterminado para la [COleVariant::COleVariant](#colevariant) constructor con una cadena o parámetro de puntero de cadena y no **VARTYPE** es UNICODE.  
  
 Un conjunto de registros DAO en una compilación no UNICODE espera que las cadenas ANSI. Por lo tanto, para DAO funciones que utilizan `COleVariant` objetos, si no va a crear un conjunto de registros UNICODE, debe utilizar el **COleVariant::COleVariant (** `lpszSrc` **,** `vtSrc` **)**  forma de constructor con `vtSrc` establecido en `VT_BSTRT` (ANSI) o use `SetString` con `vtSrc` establecido en `VT_BSTRT` hacer cadenas ANSI. Por ejemplo, el `CDaoRecordset` funciones [CDaoRecordset::Seek](../../mfc/reference/cdaorecordset-class.md#seek) y [CDaoRecordset::SetFieldValue](../../mfc/reference/cdaorecordset-class.md#setfieldvalue) usar `COleVariant` objetos como parámetros. Estos objetos deben ser ANSI si el conjunto de registros DAO no es UNICODE.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)



