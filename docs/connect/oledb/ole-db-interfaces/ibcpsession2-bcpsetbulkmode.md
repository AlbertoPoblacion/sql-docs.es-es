---
title: IBCPSession2::BCPSetBulkMode | Microsoft Docs
description: 'Uso de ibcpsession2:: Bcpsetbulkmode para crear una copia masiva una consulta o una tabla'
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- BCPSetBulkMode function
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: 5987ca7b01022d30df0ee9bcded83ec4f65078ff
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "66790739"
---
# <a name="ibcpsession2bcpsetbulkmode"></a>IBCPSession2::BCPSetBulkMode
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Ibcpsession2:: Bcpsetbulkmode proporciona una alternativa a [ibcpsession:: BCPColFmt &#40;OLE DB&#41; ](../../oledb/ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md) para especificar el formato de columna. A diferencia de ibcpsession:: BCPColFmt, que establece los atributos de formato de columna individual, ibcpsession2:: Bcpsetbulkmode establece todos los atributos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
  
HRESULT BCPSetBulkMode (  
      int property,  
   void * pField,  
   int cbField,  
   void * pRow,  
   int cbRow  
);  
```  
  
## <a name="arguments"></a>Argumentos  
 *property*  
 Constante de tipo BYTE. Vea la tabla en la sección Comentarios para obtener una lista de las constantes.  
  
 *pField*  
 Puntero al valor de terminador de campo.  
  
 cbField  
 Longitud en bytes del valor de terminador de campo.  
  
 pRow  
 Puntero al valor de terminador de fila.  
  
 cbRow  
 Longitud en bytes del valor de terminador de fila.  
  
## <a name="returns"></a>Devuelve  
 Ibcpsession2:: Bcpsetbulkmode puede devolver uno de los siguientes:  
  
|||  
|-|-|  
|**S_OK**|El método se ha llevado a cabo de forma correcta.|  
|**E_FAIL**|Se ha producido un error específico del proveedor; para obtener más información, use la interfaz ISQLServerErrorInfo.|  
|**E_UNEXPECTED**|No se esperaba la llamada al método. Por ejemplo, el **IBCPSession2::BCPInit** no se llamó al método antes de llamar a ibcpsession2:: Bcpsetbulkmode.|  
|**E_INVALIDARG**|El argumento no era válido.|  
|**E_OUTOFMEMORY**|Error de memoria insuficiente.|  
  
## <a name="remarks"></a>Notas  
 Ibcpsession2:: Bcpsetbulkmode puede utilizarse para la copia masiva de una consulta o una tabla. Cuando IBCPSession2::BCPSetBulkMode se usa para la copia masiva de una instrucción de consulta, es necesario realizar antes una llamada a `IBCPSession::BCPControl(BCP_OPTIONS_HINTS, ...)` para especificar la instrucción de consulta.  
  
 Debe evitarse combinar la sintaxis de llamada RPC con la sintaxis de consulta por lotes (`{rpc func};SELECT * from Tbl`, por ejemplo) en el texto del mismo comando,  Esto hará que ICommandPrepare:: Prepare devolver un error y le impediría recuperar metadatos. Utilice la sintaxis de ODBC CALL (`{call func}; SELECT * from Tbl`, por ejemplo) si necesita combinar la ejecución del procedimiento almacenado y la consulta por lotes en el texto del mismo comando.  
  
 En la lista siguiente se enumeran las constantes del parámetro *property* .  
  
|property|Descripción|  
|--------------|-----------------|  
|BCP_OUT_CHARACTER_MODE|Especifica el modo de salida de caracteres.<br /><br /> Se corresponde con la opción - c en BCP. EXE y a ibcpsession:: BCPColFmt con *eUserDataType* propiedad establecida en **BCP_TYPE_SQLCHARACTER**.|  
|BCP_OUT_WIDE_CHARACTER_MODE|Especifica el modo de salida de Unicode.<br /><br /> Corresponde a la opción -w de BCP. EXE e ibcpsession:: BCPColFmt con *eUserDataType* propiedad establecida en **BCP_TYPE_SQLNCHAR**.|  
|BCP_OUT_NATIVE_TEXT_MODE|Especifica los tipos nativos para los tipos no de caracteres y Unicode para los tipos de caracteres.<br /><br /> Se corresponde con la opción -N de BCP. EXE e ibcpsession:: BCPColFmt con *eUserDataType* propiedad establecida en **BCP_TYPE_SQLNCHAR** si el tipo de columna es una cadena o **BCP_TYPE_DEFAULT** si no es una cadena.|  
|BCP_OUT_NATIVE_MODE|Especifica los tipos de base de datos nativos.<br /><br /> Se corresponde con la opción - n de BCP. EXE e ibcpsession:: BCPColFmt con *eUserDataType* propiedad establecida en **BCP_TYPE_DEFAULT**.|  
  
 Puede llamar a ibcpsession:: Bcpcontrol e ibcpsession2:: Bcpsetbulkmode para ibcpsession:: Bcpcontrol opciones que no entren en conflicto con ibcpsession2:: Bcpsetbulkmode. Por ejemplo, puede llamar a ibcpsession:: Bcpcontrol con **BCP_OPTION_FIRST** e ibcpsession2:: Bcpsetbulkmode.  
  
 No se puede llamar a ibcpsession:: Bcpcontrol con **BCP_OPTION_TEXTFILE** e ibcpsession2:: Bcpsetbulkmode.  
  
 Si intenta llamar a ibcpsession2:: Bcpsetbulkmode con una secuencia de llamadas de función que incluye ibcpsession:: BCPColFmt ibcpsession:: Bcpcontrol e ibcpsession:: Bcpreadfmt, una de las llamadas de función devolverá un error de secuencia. Si elige corregir el error, llame a IBCPSession::BCPInit para restablecer los valores de configuración y volver a empezar.  
  
 A continuación se muestran algunos ejemplos de llamadas de función que se producirá un error de secuencia de función:  
  
```cpp  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_IN);  
BCPSetBulkMode();  
```  
  
```cpp  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPSetBulkMode();  
BCPReadFmt();  
```  
  
```cpp  
BCPInit(NULL, "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_HINTS, "select ...");  
BCPSetBulkMode();  
```  
  
```cpp  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPSetBulkMode();  
BCPColFmt();  
```  
  
```cpp  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_DELAYREADFMT, true);  
BCPReadFmt();  
BCPColFmt();  
```  
  
```cpp  
BCPInit(NULL, "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_DELAYREADFMT, true);  
BCPSetBulkMode();  
BCPControl(BCP_OPTION_HINTS, "select ...");  
BCPReadFmt();  
```  
  
```cpp  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_DELAYREADFMT, true);  
BCPColumns();  
```  
  
```cpp  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_DELAYREADFMT, true);  
BCPSetColFmt();  
```  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se crean cuatro archivos con valores distintos de IBCPSession2::BCPSetBulkMode.  
  
```cpp  
  
// compile with: oleaut32.lib ole32.lib  
  
#include <stdio.h>  
#include "msoledbsql.h"  
  
IDBInitialize*  g_pIDBInitialize = NULL;  
IBCPSession2 * g_pIBcpSession = NULL;  
class COLEDBPropSet : public DBPROPSET {  
public:  
   COLEDBPropSet() {  
      rgProperties = NULL;  
      cProperties = 0;  
   };  
   COLEDBPropSet(const GUID& guid) {  
      rgProperties = NULL;  
      cProperties = 0;  
      guidPropertySet = guid;  
   };  
   ~COLEDBPropSet() {  
      for ( ULONG i = 0 ; i < cProperties ; i++ )  
         VariantClear(&rgProperties[i].vValue);  
      CoTaskMemFree(rgProperties);  
   }  
   void SetGUID(const GUID& guid) {  
      guidPropertySet = guid;  
   };  
   bool AddProperty(DWORD dwPropertyID, bool bValue) {  
      if (!Add())  
         return false;  
      rgProperties[cProperties].dwPropertyID = dwPropertyID;  
      rgProperties[cProperties].vValue.vt = VT_BOOL;  
      rgProperties[cProperties].vValue.boolVal = (bValue) ? VARIANT_TRUE : VARIANT_FALSE;  
      cProperties++;  
      return true;  
   };  
   bool AddProperty(DWORD dwPropertyID, long nValue) {  
      if (!Add())  
         return false;  
      rgProperties[cProperties].dwPropertyID  = dwPropertyID;  
      rgProperties[cProperties].vValue.vt     = VT_I4;  
      rgProperties[cProperties].vValue.lVal   = nValue;  
      cProperties++;  
      return true;  
   };  
   bool AddProperty(DWORD dwPropertyID,LPCWSTR szValue) {  
      if (!Add())  
         return false;  
      rgProperties[cProperties].dwPropertyID = dwPropertyID;  
      rgProperties[cProperties].vValue.vt = VT_BSTR;  
      rgProperties[cProperties].vValue.bstrVal = SysAllocString(szValue);  
      cProperties++;  
      return true;  
   };  
   bool Add() {  
      DBPROP* p = (DBPROP*)CoTaskMemRealloc(rgProperties, (cProperties + 1) * sizeof(DBPROP));  
      if (p != NULL) {  
         rgProperties = p;  
         rgProperties[cProperties].dwOptions = DBPROPOPTIONS_REQUIRED;  
         rgProperties[cProperties].colid = DB_NULLID;  
         rgProperties[cProperties].vValue.vt = VT_EMPTY;  
         return true;  
      }  
      else  
         return false;  
   };  
};  
  
void OLEDBCleanUp() {  
   if (g_pIDBInitialize) {  
      g_pIDBInitialize->Release();  
      g_pIDBInitialize = NULL;  
   }  
   if (g_pIBcpSession) {  
      g_pIBcpSession->Release();  
      g_pIBcpSession = NULL;  
   }  
}  
  
BOOL MakeOLEDBConnect(LPWSTR  pServer) {  
   BOOL ret = true;  
   IDBProperties * pIDBProperties = NULL;  
   IDBCreateSession * pIDBCreateSession = NULL;  
   COLEDBPropSet PropSet(DBPROPSET_DBINIT);  
   COLEDBPropSet BcpProperty(DBPROPSET_SQLSERVERDATASOURCE);  
   try {  
      HRESULT hr = CoInitializeEx(NULL,COINIT_MULTITHREADED);   
      hr = CoCreateInstance(MSOLEDBSQL_CLSID, NULL, CLSCTX_INPROC_SERVER, IID_IDBInitialize, (LPVOID *)&g_pIDBInitialize);  
      if (FAILED(hr)) {  
         printf("CoCreateInstance failed\n");  
         return false;  
      }  
      PropSet.AddProperty(DBPROP_INIT_DATASOURCE, (LPWSTR)pServer);  
      PropSet.AddProperty(DBPROP_AUTH_INTEGRATED, L"SSPI");  
      hr = g_pIDBInitialize->QueryInterface(IID_IDBProperties, (void**) &pIDBProperties);  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->->QueryInterface(IID_IDBProperties...) failed\n");  
         throw false;  
      }  
      hr = pIDBProperties->SetProperties(1, &PropSet);  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->->SetProperties(...) failed\n");  
         throw false;  
      }  
      hr = g_pIDBInitialize->Initialize();  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->->Initialize() failed\n");  
         throw false;  
      }  
      BcpProperty.AddProperty(SSPROP_ENABLEFASTLOAD, true);  
      BcpProperty.AddProperty(SSPROP_ENABLEBULKCOPY, true);  
      hr = pIDBProperties->SetProperties(1, &BcpProperty);  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->->SetProperties() for bcp failed\n");  
         throw false;  
      }  
      hr = g_pIDBInitialize->QueryInterface(IID_IDBCreateSession, (void**) &pIDBCreateSession);  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->QueryInterface(IID_IDBCreateSession..) failed\n");  
         throw false;  
      }  
  
      hr = pIDBCreateSession->CreateSession(NULL, IID_IBCPSession2, (IUnknown**) &g_pIBcpSession);  
      if (FAILED(hr)) {  
         printf("g_pIDBCreateSession->CreateSession() failed\n");  
         throw false;  
      }  
   }  
   catch(...) {  
      ret = false;  
   }  
   if (pIDBProperties)  
      pIDBProperties->Release();  
   if (pIDBCreateSession)  
      pIDBCreateSession->Release();  
   return ret;  
}  
  
BOOL BCPSetBulkMode(LPWSTR pszServer, LPTSTR pszQureryOut, char BCPType, LPWSTR pszDataFile) {  
   HRESULThr;  
   if (!MakeOLEDBConnect(pszServer))  
      return false;  
   hr = g_pIBcpSession->BCPInit(NULL, pszDataFile, NULL, BCP_DIRECTION_OUT );   // bcp init for queryout  
   if (FAILED(hr)) {  
      printf("BCP init failed\n");  
      OLEDBCleanUp();  
      return false;  
   }  
   // setbulkmode  
   char ColTerm[] = "\t";  
   char RowTerm[] = "\r\n";  
   wchar_t wColTerm[] = L"\t";  
   wchar_t wRowTerm[] = L"\r\n";  
   BYTE * pColTerm = NULL;  
   int cbColTerm = NULL;  
   BYTE * pRowTerm = 0;  
   int cbRowTerm = 0;  
   int bulkmode = -1;  
  
   if(BCPType == 'c') {   // bcp -c  
      pColTerm = (BYTE*)ColTerm;  
      pRowTerm = (BYTE*)RowTerm;  
      cbColTerm = 1;  
      cbRowTerm = 2;  
      bulkmode = BCP_OUT_CHARACTER_MODE;  
   }  
   else  
      if(BCPType == 'w') {   // bcp -w  
         pColTerm = (BYTE*)wColTerm;  
         pRowTerm = (BYTE*)wRowTerm;  
         cbColTerm = 2;  
         cbRowTerm = 4;  
         bulkmode = BCP_OUT_WIDE_CHARACTER_MODE;  
      }  
      else  
         if (BCPType == 'n')   // bcp -n  
            bulkmode = BCP_OUT_NATIVE_MODE;  
         else  
            if (BCPType == 'N')   // bcp -n  
               bulkmode = BCP_OUT_NATIVE_TEXT_MODE;  
            else {  
               printf("unknown bcp mode\n");  
               OLEDBCleanUp();  
               return false;  
            }  
            hr = g_pIBcpSession->BCPSetBulkMode(bulkmode, pColTerm, cbColTerm, pRowTerm, cbRowTerm);  
            if (FAILED(hr)) {  
               printf("BCPSetBulkMode failed\n");  
               OLEDBCleanUp();  
               return false;  
            }  
  
            // set queryout TSQL statement  
            hr = g_pIBcpSession->BCPControl(BCP_OPTION_HINTS, pszQureryOut);  
            if (FAILED(hr)) {  
               printf("BCPControl failed\n");  
               OLEDBCleanUp();  
               return false;  
            }  
            // bcp copy  
            DBROWCOUNT nRowsInserted = 0;  
            hr = g_pIBcpSession->BCPExec(&nRowsInserted);  
            if (FAILED(hr)) {  
               printf("BCPExec failed\n");  
               OLEDBCleanUp();  
               return false;  
            }  
            printf("bcp done\n");  
            OLEDBCleanUp();  
            return true;  
}  
  
int main() {  
   BCPSetBulkMode(L"localhost", TEXT("SELECT 'this is a bcp -c test', 1,2") , 'c', L"bcpc.dat");  
   BCPSetBulkMode(L"localhost", TEXT("SELECT 'this is a bcp -w test', 1,2") , 'w', L"bcpw.dat");  
   BCPSetBulkMode(L"localhost", TEXT("SELECT 'this is a bcp -c test', 1,2") , 'n', L"bcpn.dat");  
   BCPSetBulkMode(L"localhost", TEXT("SELECT 'this is a bcp -w test', 1,2") , 'N', L"bcp_N.dat");  
}  
```  
  
## <a name="see-also"></a>Consulte también  
 [IBCPSession2 &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession2-ole-db.md)  
  
  
