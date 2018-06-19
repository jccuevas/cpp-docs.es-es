---
title: Clase CRecentFileList | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CRecentFileList
- AFXADV/CRecentFileList
- AFXADV/CRecentFileList::CRecentFileList
- AFXADV/CRecentFileList::Add
- AFXADV/CRecentFileList::GetDisplayName
- AFXADV/CRecentFileList::GetSize
- AFXADV/CRecentFileList::ReadList
- AFXADV/CRecentFileList::Remove
- AFXADV/CRecentFileList::UpdateMenu
- AFXADV/CRecentFileList::WriteList
dev_langs:
- C++
helpviewer_keywords:
- CRecentFileList [MFC], CRecentFileList
- CRecentFileList [MFC], Add
- CRecentFileList [MFC], GetDisplayName
- CRecentFileList [MFC], GetSize
- CRecentFileList [MFC], ReadList
- CRecentFileList [MFC], Remove
- CRecentFileList [MFC], UpdateMenu
- CRecentFileList [MFC], WriteList
ms.assetid: a77f0524-7584-4582-849a-7e97b76d186e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 337ecf8227f1d5c2abe0369abdea5662f882f3d2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33377258"
---
# <a name="crecentfilelist-class"></a>Clase CRecentFileList
Admite el control de lista de los archivos utilizados más recientemente (MRU).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CRecentFileList  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRecentFileList::CRecentFileList](#crecentfilelist)|Construye un objeto `CRecentFileList`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRecentFileList::Add](#add)|Agrega un archivo a la lista de archivos utilizados más Recientemente.|  
|[CRecentFileList::GetDisplayName](#getdisplayname)|Proporciona un nombre para mostrar para la visualización de menú de un nombre de archivo de elementos utilizados Recientemente.|  
|[CRecentFileList::GetSize](#getsize)|Recupera el número de archivos en la lista de archivos utilizados más Recientemente.|  
|[CRecentFileList::ReadList](#readlist)|Lee la lista de archivos utilizados más Recientemente desde el registro o. Archivo INI.|  
|[CRecentFileList::Remove](#remove)|Quita un archivo de la lista de archivos utilizados más Recientemente.|  
|[CRecentFileList::UpdateMenu](#updatemenu)|Actualiza la presentación de menú de la lista de archivos utilizados más Recientemente.|  
|[CRecentFileList::WriteList](#writelist)|Escribe la lista de archivos utilizados más Recientemente desde el registro o. Archivo INI.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[[] CRecentFileList::operator](#operator_at)|Devuelve un `CString` objeto en una posición determinada.|  
  
## <a name="remarks"></a>Comentarios  
 Los archivos se pueden agregar a o elimina de la lista de archivos utilizados más Recientemente, la lista de archivos se puede leer o escribir en el registro o un. Pueden actualizar el archivo .ini y el menú de mostrar la lista de archivos utilizados más Recientemente.  
  
 Para obtener más información acerca de los elementos de menú de elementos utilizados Recientemente, vea  
  
-   El artículo de Knowledge Base Q243751: Cómo: agregar controladores de comandos para elementos de menú utilizados más Recientemente en la aplicación MFC  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CRecentFileList`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxadv.h  
  
##  <a name="add"></a>  CRecentFileList::Add  
 Agrega un archivo a la lista de archivos usa más recientemente (MRU).  
  
```  
virtual void Add(LPCTSTR lpszPathName);

 
virtual void Add(
    LPCTSTR lpszPathName,
    LPCTSTR lpszAppID);

 
void Add(
    IShellItem* pItem,
    LPCTSTR lpszAppID);

 
void Add(
    IShellLink* pLink,
    LPCTSTR lpszAppID);

 
void Add(
    PIDLIST_ABSOLUTE pidl,
    LPCTSTR lpszAppID);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszPathName`  
 Especifica la ruta de acceso para agregarse a la lista.  
  
 `lpszAppID`  
 Especifica el identificador del modelo de aplicación de usuario para la aplicación.  
  
 `pItem`  
 Especifica un puntero al elemento de Shell para agregarse a la lista.  
  
 `pLink`  
 Especifica un puntero al vínculo de Shell para agregarse a la lista.  
  
 `pidl`  
 Especifica al LISTA_ID para el elemento de shell que debe agregarse a la carpeta de documentos recientes.  
  
### <a name="remarks"></a>Comentarios  
 El nombre de archivo se agregará a la parte superior de la lista de elementos utilizados Recientemente. Si el nombre de archivo ya existe en la lista de elementos utilizados Recientemente, se moverán a la parte superior.  
  
##  <a name="crecentfilelist"></a>  CRecentFileList::CRecentFileList  
 Construye un objeto `CRecentFileList`.  
  
```  
CRecentFileList(
    UINT nStart,  
    LPCTSTR lpszSection,  
    LPCTSTR lpszEntryFormat,  
    int nSize,  
    int nMaxDispLen = AFX_ABBREV_FILENAME_LEN);
```  
  
### <a name="parameters"></a>Parámetros  
 `nStart`  
 Desplazamiento de la numeración en la pantalla de menú de la lista de archivos utilizados más Recientemente (usado más recientemente).  
  
 `lpszSection`  
 Señala al nombre de la sección del registro o la aplicación. Archivo .ini donde la lista de archivos utilizados más Recientemente es leída y/o escrita.  
  
 `lpszEntryFormat`  
 Apunta a una cadena de formato que se utilizará para los nombres de las entradas almacenadas en el registro o la aplicación. Archivo INI.  
  
 `nSize`  
 Número máximo de archivos en la lista de archivos utilizados más Recientemente.  
  
 `nMaxDispLen`  
 Longitud máxima, en caracteres, disponibles para la presentación de menú de un nombre de archivo en la lista de archivos utilizados más Recientemente.  
  
### <a name="remarks"></a>Comentarios  
 La cadena de formato que señala `lpszEntryFormat` debe contener "%d", que se usará para sustituir el índice de cada elemento de elementos utilizados Recientemente. Por ejemplo, si la cadena de formato es `"file%d"` , a continuación, las entradas se denominará `file0`, `file1`, y así sucesivamente.  
  
##  <a name="getdisplayname"></a>  CRecentFileList::GetDisplayName  
 Obtiene un nombre para mostrar de un archivo en la lista de archivos utilizados más Recientemente, para su uso en la pantalla de menú de la lista de elementos utilizados Recientemente.  
  
```  
virtual BOOL GetDisplayName(
    CString& strName,  
    int nIndex,  
    LPCTSTR lpszCurDir,  
    int nCurDir,  
    BOOL bAtLeastName = TRUE) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `strName`  
 Ruta de acceso completa del archivo cuyo nombre se mostrará en la lista del menú de archivos utilizados más Recientemente.  
  
 `nIndex`  
 Índice de base cero del archivo en la lista de archivos utilizados más Recientemente.  
  
 *lpszCurDir*  
 Cadena que contiene el directorio actual.  
  
 *nCurDir*  
 Longitud de la cadena del directorio actual.  
  
 `bAtLeastName`  
 Si es distinto de cero, indica que se debe devolver el nombre base del archivo, incluso si supera la longitud máxima de visualización (pasado como el `nMaxDispLen` parámetro para el `CRecentFileList` constructor).  
  
### <a name="return-value"></a>Valor devuelto  
 **FALSE** si no hay ningún nombre de archivo en el índice especificado en la lista de archivos usa más recientemente (MRU).  
  
### <a name="remarks"></a>Comentarios  
 Si el archivo está en el directorio actual, la función deja el directorio de la pantalla. Si el nombre de archivo es demasiado largo, se eliminan el directorio y la extensión. Si el nombre de archivo sigue siendo demasiado largo, el nombre para mostrar se establece en una cadena vacía a menos que `bAtLeastName` es distinto de cero.  
  
##  <a name="getsize"></a>  CRecentFileList::GetSize  
 Recupera el número de archivos en la lista de archivos utilizados más Recientemente.  
  
```  
int GetSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de archivos actual más archivos usados recientemente (MRU).  
  
##  <a name="operator_at"></a>  [] CRecentFileList::operator  
 El subíndice sobrecargado ( `[]`) operador devuelve un valor single `CString` especificado por el índice de base cero en `nIndex`.  
  
```  
CString& operator[ ](int nindex);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice de base cero de un `CString` en un conjunto de `CString`s.  
  
##  <a name="readlist"></a>  CRecentFileList::ReadList  
 Lee la mayoría de la archivos usados recientemente (MRU) desde el registro o la aplicación. Archivo INI.  
  
```  
virtual void ReadList();
```  
  
##  <a name="remove"></a>  CRecentFileList::Remove  
 Quita un archivo de la lista de archivos utilizados más Recientemente.  
  
```  
virtual void Remove(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice de base cero del archivo que se va a quitar de la lista de archivos usa más recientemente (MRU).  
  
##  <a name="updatemenu"></a>  CRecentFileList::UpdateMenu  
 Actualiza la presentación de menú de la lista de archivos utilizados más Recientemente.  
  
```  
virtual void UpdateMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Parámetros  
 `pCmdUI`  
 Un puntero a la [CCmdUI](../../mfc/reference/ccmdui-class.md) objeto para el menú de lista de usados recientemente (MRU) archivo.  
  
##  <a name="writelist"></a>  CRecentFileList::WriteList  
 Escribe la mayoría de la archivos usados recientemente (MRU) en el registro o la aplicación. Archivo INI.  
  
```  
virtual void WriteList();
```  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)



