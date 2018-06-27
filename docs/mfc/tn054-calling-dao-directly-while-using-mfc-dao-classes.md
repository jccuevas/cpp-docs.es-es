---
title: 'TN054: Llamar a DAO directamente mientras se usan clases DAO de MFC | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.dao
dev_langs:
- C++
helpviewer_keywords:
- MFC, DAO and
- passwords [MFC], calling DAO
- security [MFC], DAO
- DAO (Data Access Objects), calling directly
- DAO (Data Access Objects), security
- security [MFC]
- TN054
- DAO (Data Access Objects), and MFC
ms.assetid: f7de7d85-8d6c-4426-aa05-2e617c0da957
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8ed0fc9a18278c4e603b9ddae5197f6b5d03ee21
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36950952"
---
# <a name="tn054-calling-dao-directly-while-using-mfc-dao-classes"></a>TN054: Llamar a DAO directamente mientras se usan clases DAO de MFC
> [!NOTE]
>  El entorno de Visual C++ y los asistentes no admiten DAO (aunque las clases DAO están incluidas y puede seguir usándolos). Microsoft recomienda que utilice [plantillas OLE DB](../data/oledb/ole-db-templates.md) o [ODBC y MFC](../data/odbc/odbc-and-mfc.md) para los nuevos proyectos. Solo debería utilizar DAO para mantener las aplicaciones existentes.  
  
 Al utilizar las clases de base de datos DAO de MFC, puede haber situaciones en las que es necesario utilizar DAO directamente. Normalmente, esto no es el caso, pero MFC ha proporcionado algunos mecanismos de aplicación auxiliar para facilitar la realización llamadas directas DAO simple al combinar el uso de las clases MFC con las llamadas directas a DAO. DAO directa de realizar llamadas a los métodos de un objeto DAO de MFC administrados es necesario solo unas pocas líneas de código. Si necesita crear y utilizar objetos DAO *no* administrados por MFC, tendrá que trabajar un poco más llamando realmente `Release` en el objeto. Esta nota técnica explica cuando desee llamar a DAO directamente, lo que pueden hacer las aplicaciones auxiliares MFC para ayudarle a y cómo usar las interfaces OLE de DAO. Por último, esta nota proporciona algunas funciones de ejemplo que muestra cómo llamar a DAO directamente para las características de seguridad DAO.  
  
## <a name="when-to-make-direct-dao-calls"></a>Cuándo se deben realizar llamadas directas de DAO  
 Se producen las situaciones más comunes para realizar llamadas DAO directas cuando las colecciones tienen que actualizarse o cuando se implementan características que no están encapsuladas por MFC. La característica más importante no expuesta MFC es la seguridad. Si desea implementar características de seguridad, debe utilizar los objetos User (s) de DAO y grupos directamente. Además de la seguridad, hay solo unos pocos otros DAO características no admitidas por MFC. Estos incluyen características de replicación de base de datos y clonación de conjunto de registros, así como algunas adiciones de tiempo de ejecución a DAO.  
  
## <a name="a-brief-overview-of-dao-and-mfcs-implementation"></a>Una breve descripción de la implementación de MFC y DAO  
 Ajuste de MFC facilita la DAO mediante DAO más fácil de administrar muchos de los detalles de por lo que no tiene que preocuparse de las cosas. Esto incluye la inicialización de OLE, la creación y administración de los objetos DAO (especialmente en los objetos de colección), error de comprobación y proporcionar una interfaz más sencilla, fuertemente tipada (no **VARIANT** o `BSTR` argumentos). Puede realizar llamadas directas a DAO y seguir aprovechando estas características. Todo el código no debe hacer es llamada `Release` para los objetos creados por DAO directa llama y *no* modificar cualquiera de los punteros de interfaz MFC puede basarse en internamente. Por ejemplo, no modifique la *m_pDAORecordset* miembro de un formato de archivo `CDaoRecordset` objeto a menos que entienda *todos los* las ramificaciones internas. Sin embargo, puede utilizar el *m_pDAORecordset* interfaz para llamar a DAO directamente para obtener la colección de campos. En este caso el *m_pDAORecordset* miembro no debería modificarse. Solo tiene que llamar a `Release` en el objeto de colección de campos cuando haya terminado con el objeto.  
  
## <a name="description-of-helpers-to-make-dao-calls-easier"></a>Descripción de las aplicaciones auxiliares para realizar DAO llama sea más fácil  
 Las aplicaciones auxiliares proporcionadas para realizar una llamada a DAO más fácil son el mismo las aplicaciones auxiliares que se usan internamente en las clases de base de datos de DAO de MFC. Estas aplicaciones auxiliares se utilizan para comprobar los códigos de retorno al realizar una llamada directa de DAO, registro de salida de depuración, comprueba si hay errores esperados y producir excepciones adecuadas si es necesario. Hay dos funciones auxiliares subyacente y cuatro macros que se asignan a uno de estos dos programas. La mejor explicación sería simplemente leer el código. Vea **DAO_CHECK**, **DAO_CHECK_ERROR**, **DAO_CHECK_MEM**, y **DAO_TRACE** en AFXDAO. H para ver las macros y ver **AfxDaoCheck** y **AfxDaoTrace** en DAOCORE. CPP.  
  
## <a name="using-the-dao-ole-interfaces"></a>Uso de las Interfaces OLE de DAO  
 Las interfaces OLE para cada objeto en la jerarquía de objetos DAO se definen en el archivo de encabezado DBDAOINT. H, que se encuentra en el directorio \Program 2003\VC7\include de Visual Studio. NET. Estas interfaces proporcionan métodos que permiten manipular toda la jerarquía DAO.  
  
 Para muchos de los métodos de las interfaces DAO, es necesario manipular un `BSTR` objeto (una cadena de longitud fija utilizada en la automatización OLE). El `BSTR` objeto normalmente se encapsula dentro de la **VARIANT** tipo de datos. La clase MFC `COleVariant` a su vez hereda de la **VARIANT** tipo de datos. Dependiendo de si genera el proyecto de ANSI o Unicode, las interfaces DAO devolverá ANSI o Unicode `BSTR`s. Dos macros, V_BSTR y V_BSTRT, son útiles para asegurarse de que la interfaz DAO Obtiene el `BSTR` del tipo esperado.  
  
 V_BSTR extraerá el *bstrVal* miembro de un `COleVariant`. Esta macro se usa normalmente cuando es necesario pasar el contenido de un `COleVariant` a un método de una interfaz de DAO. El fragmento de código siguiente muestra las declaraciones y el uso real para los dos métodos de la interfaz de DAO DAOUser que sacar partido de la macro V_BSTR:  
  
```  
COleVariant varOldName;  
COleVariant varNewName(_T("NewUser"), VT_BSTRT);

 
// Code to assign pUser to a valid value omitted  
DAOUser *pUser = NULL;  
 
// These method declarations were taken from DBDAOINT.H  
// STDMETHOD(get_Name) (THIS_ BSTR FAR* pbstr) PURE;  
// STDMETHOD(put_Name) (THIS_ BSTR bstr) PURE;  
 
DAO_CHECK(pUser->get_Name(&V_BSTR (&varOldName)));

DAO_CHECK(pUser->put_Name(V_BSTR (&varNewName)));
```  
  
 Tenga en cuenta que la `VT_BSTRT` argumento especificado en el `COleVariant` constructor anterior garantiza que habrá un ANSI `BSTR` en el `COleVariant` si se compila una versión de ANSI de la aplicación y Unicode `BSTR` para una versión Unicode de la aplicación. Esto es lo que espera DAO.  
  
 Otras macros, V_BSTRT, extraerá ANSI o Unicode *bstrVal* miembro de `COleVariant` según el tipo de compilación (ANSI o Unicode). El código siguiente muestra cómo extraer el `BSTR` valor desde una `COleVariant` en un `CString`:  
  
```  
COleVariant varName(_T("MyName"), VT_BSTRT);

CString str = V_BSTRT(&varName);
```  
  
 La macro V_BSTRT, junto con otras técnicas para abrir otros tipos que se almacenan en `COleVariant`, se muestra en el ejemplo DAOVIEW. En concreto, esta conversión se realiza en el `CCrack::strVARIANT` método. Este método, siempre que sea posible, convierta el valor de un `COleVariant` en una instancia de `CString`.  
  
## <a name="simple-example-of-a-direct-call-to-dao"></a>Ejemplo sencillo de una llamada directa a DAO  
 Pueden surgir situaciones cuando sea necesario actualizar los objetos de colección DAO subyacentes. Normalmente, esto no debería ser necesario, pero es un procedimiento simple si es necesario. Un ejemplo de cuándo una colección deba actualizarse es cuando se trabaja en un entorno multiusuario con varios usuarios crear nuevas definiciones de tabla. En este caso el tabledefs (colección) podría se conviertan en obsoleta. Para actualizar la colección, basta con llamar a la `Refresh` método del objeto de colección en particular y compruebe si hay errores:  
  
```  
DAO_CHECK(pMyDaoDatabase->  
    m_pDAOTableDefs->Refresh());
```  
  
 Tenga en cuenta que, actualmente, todas las interfaces del objeto de colección de DAO son detalles de implementación no documentadas de las clases de base de datos DAO de MFC.  
  
## <a name="using-dao-directly-for-dao-security-features"></a>Uso de DAO directamente para las características de seguridad DAO  
 Las clases de base de datos DAO de MFC no ajustan las características de seguridad DAO. Debe llamar a métodos de las interfaces DAO para utilizar algunas características de seguridad DAO. La función siguiente establece la base de datos del sistema y, a continuación, cambia la contraseña del usuario. Esta función llama a tres otras funciones, que posteriormente se definen.  
  
```  
void ChangeUserPassword()  
{ *// Specify path to the Microsoft Access *// system database  
    CString strSystemDB = 
    _T("c:\\Program Files\\MSOffice\\access\\System.mdw");

 *// Set system database before MFC initilizes DAO *// NOTE: An MFC module uses only one instance *// of a DAO database engine object. If you have *// called a DAO object in your application prior *// to calling the function below,
    you must call *// AfxDaoTerm to destroy the existing database *// engine object. Otherwise,
    the database engine *// object already in use will be reused,
    and setting *// a system datbase will have no effect. *// *// If you have used a DAO object prior to calling *// this function it is important that DAO be *// terminated with AfxDaoTerm since an MFC *// module only gets one copy of the database engine *// and that engine will be reused if it hasn't been *// terminated. In other words,
    if you do not call *// AfxDaoTerm and there is currently a database *// initialized,
    setting the system database will *// have no affect.  
 
    SetSystemDB(strSystemDB);

 *// User name and password manually added *// by using Microsoft Access  
    CString strUserName = _T("NewUser");

    CString strOldPassword = _T("Password");

    CString strNewPassword = _T("NewPassword");

 *// Set default user so that MFC will be able *// to log in by default using the user name and *// password from the system database  
    SetDefaultUser(strUserName,
    strOldPassword);

 *// Change the password. You should be able to *// call this function from anywhere in your *// MFC application  
    ChangePassword(strUserName,
    strOldPassword,   
    strNewPassword);

 
 .  
 .  
 .  
 
}  
```  
  
 Los siguientes cuatro ejemplos muestran cómo:  
  
-   Establecer la base de datos DAO (. Archivo MDW).  
  
-   Establecer el usuario predeterminado y la contraseña.  
  
-   Cambie la contraseña de un usuario.  
  
-   Cambiar la contraseña de una. Archivo MDB.  
  
### <a name="setting-the-system-database"></a>Configuración de la base de datos del sistema  
 A continuación se muestra una función de ejemplo para establecer la base de datos que se usará en una aplicación. Esta función debe llamarse antes de realizan otras llamadas de DAO.  
  
```  
// Set the system database that the   
// DAO database engine will use  
 
void SetSystemDB(CString& strSystemMDB)  
{  
    COleVariant varSystemDB(strSystemMDB, VT_BSTRT);

 *// Initialize DAO for MFC  
    AfxDaoInit();
DAODBEngine* pDBEngine = AfxDaoGetEngine();

 
    ASSERT(pDBEngine != NULL);

 *// Call put_SystemDB method to set the *// system database for DAO engine  
    DAO_CHECK(pDBEngine->put_SystemDB(varSystemDB.bstrVal));

} 
```  
  
### <a name="setting-the-default-user-and-password"></a>Establecer el usuario predeterminado y la contraseña  
 Para establecer el usuario predeterminado y la contraseña para una base de datos del sistema, utilice la siguiente función:  
  
```  
void SetDefaultUser(CString& strUserName,
    CString& strPassword)  
{  
    COleVariant varUserName(strUserName,
    VT_BSTRT);

    COleVariant varPassword(strPassword,
    VT_BSTRT);

 
    DAODBEngine* pDBEngine = AfxDaoGetEngine();
ASSERT(pDBEngine != NULL);

 *// Set default user:  
    DAO_CHECK(pDBEngine->put_DefaultUser(varUserName.bstrVal));

 *// Set default password:  
    DAO_CHECK(pDBEngine->put_DefaultPassword(varPassword.bstrVal));

} 
```  
  
### <a name="changing-a-users-password"></a>Cambiar la contraseña de un usuario  
 Para cambiar la contraseña de un usuario, utilice la siguiente función:  
  
```  
void ChangePassword(CString &strUserName,   
    CString &strOldPassword,   
    CString &strNewPassword)  
{ *// Create (open) a workspace  
    CDaoWorkspace wsp;  
    CString strWspName = _T("Temp Workspace");

 
    wsp.Create(strWspName, strUserName,  
    strOldPassword);

 wsp.Append();

 *// Determine how many objects there are *// in the Users collection  
    short nUserCount;  
    short nCurrentUser;  
    DAOUser *pUser = NULL;  
    DAOUsers *pUsers = NULL;  
 *// Side-effect is implicit OLE AddRef() *// on DAOUser object:  
    DAO_CHECK(wsp.m_pDAOWorkspace->get_Users(&pUsers));

 *// Side-effect is implicit OLE AddRef() *// on DAOUsers object  
    DAO_CHECK(pUsers->getcount(&nUserCount));

 *// Traverse through the list of users *// and change password for the userid *// used to create/open the workspace  
    for(nCurrentUser = 0; nCurrentUser <nUserCount;  
    nCurrentUser++) 
 {  
    COleVariant varIndex(nCurrentUser, VT_I2);

    COleVariant varName;  
 *// Retrieve information for user nCurrentUser  
    DAO_CHECK(pUsers->get_Item(varIndex, &pUser));

 *// Retrieve name for user nCurrentUser  
    DAO_CHECK(pUser->get_Name(&V_BSTR(&varName)));

 
    CString strTemp = V_BSTRT(&varName);

 *// If there is a match, change the password  
    if(strTemp == strUserName)  
 {  
    COleVariant varOldPwd(strOldPassword,   
    VT_BSTRT);

 COleVariant  varNewPwd(strNewPassword,   
    VT_BSTRT);

 
    DAO_CHECK(pUser->NewPassword(V_BSTR(&varOldPwd), 
    V_BSTR(&varNewPwd)));

 
    TRACE("\t Password is changed\n");

 }  
 }  
 *// Clean up: decrement the usage count *// on the OLE objects  
    pUser->Release();
pUsers->Release();

 
    wsp.Close();

} 
```  
  
### <a name="changing-the-password-of-an-mdb-file"></a>Cambiar la contraseña de una. Archivo MDB  
 Para cambiar la contraseña de una. MDB de archivos, utilice la siguiente función:  
  
```  
void SetDBPassword(LPCTSTR pDB,
    LPCTSTR pszOldPassword,
    LPCTSTR pszNewPassword)  
{  
    CDaoDatabase db;  
    CString strConnect(_T(";pwd="));

 *// the database must be opened as exclusive *// to set a password  
    db.Open(pDB,
    TRUE,
    FALSE,   
    strConnect + pszOldPassword);

 
    COleVariant NewPassword(pszNewPassword,
    VT_BSTRT),  
    OldPassword(pszOldPassword,
    VT_BSTRT);

 
    DAO_CHECK(db.m_pDAODatabase->NewPassword(V_BSTR(&OldPassword), 
    V_BSTR(&NewPassword)));

 
    db.Close();

} 
```  
  
## <a name="see-also"></a>Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

