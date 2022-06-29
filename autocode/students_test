package coverage

import (
	"os"
	"time"
	"testing"
	"errors"
	"strconv"
)

// DO NOT EDIT THIS FUNCTION
func init() {
	content, err := os.ReadFile("students_test.go")
	if err != nil {
		panic(err)
	}
	err = os.WriteFile("autocode/students_test", content, 0644)
	if err != nil {
		panic(err)
	}
}

// WRITE YOUR CODE BELOW

func TestLen (t *testing.T)  {

	tDataLen:= map[string]struct {
	   People
	   wantLen int
	}{
	   "zero": {[]Person{},0 },
	   "three" : {[]Person{
		   {firstName: "James",lastName: "Goodman", birthDay: time.Date(2009, time.November, 10, 23, 0, 0, 0, time.UTC)},
		   {firstName: "Mike",lastName: "Vazovski", birthDay: time.Date(2009, time.November, 10, 23, 0, 0, 0, time.UTC)},
		   {firstName: "Arnold",lastName: "Shwarzeneger", birthDay: time.Date(2009, time.November, 10, 23, 0, 0, 0, time.UTC)},
	   },3},
	}
	for key, test := range tDataLen {
	   got:=test.People.Len()
	   if test.wantLen!=got {
		   t.Errorf("test name %s is fail",key)
	   }
	}
   }
   func TestLess(t *testing.T)  {
	   
	   peopleTestDate :=  People {
	   {firstName: "James",lastName: "Freeman", birthDay: time.Date(2012, time.November, 10, 23, 0, 0, 0, time.UTC)},
	   {firstName: "James",lastName: "Goodman", birthDay: time.Date(2012, time.November, 10, 23, 0, 0, 0, time.UTC)},
	   {firstName: "Mike",lastName: "Vazovski", birthDay: time.Date(2012, time.November, 10, 23, 0, 0, 0, time.UTC)},
	   {firstName: "Arnold",lastName: "Shwarzeneger", birthDay: time.Date(2013, time.November, 10, 23, 0, 0, 0, time.UTC)},
	   {firstName: "Jeck",lastName: "Shwarzeneger", birthDay: time.Date(2013, time.November, 10, 23, 0, 0, 0, time.UTC)},
	   }
	   tests := map[string]struct{
		   i int
		   j int
		   want bool
		}{
		   "Test 1: Different only lastName": {i: 0,j: 1,want: true},
		   "Test 2: Different only lastName (revert test 1)": {i: 1,j: 0,want: false},
		   "Test 3: Different Year Birthday": {i: 2,j: 3,want: false},
		   "Test 4: Different Year Birthday(revert test 3)": {i: 3,j: 2,want: true},
		   "Test 5: Different only Firsname": {i: 3,j: 4,want: true},
		   "Test 6: Different only Firsname (revert test 4)": {i: 4,j: 3,want: false},
		}
		for key, test := range tests {
		   got:=peopleTestDate.Less(test.i,test.j)
		   if got!=test.want {
			   t.Errorf("test name: %s", key)
		   }
	   }
	
   }
   func TestSwapPeople(t *testing.T)()  {
	   tests:=map[string]struct{
		   firs int
		   second int
		   date People
		   want People
	   }{
		   "Swap: First test":{firs: 0,second: 1,
			   date: People {
			   {firstName: "James",lastName: "Freeman", birthDay: time.Date(2012, time.November, 10, 23, 0, 0, 0, time.UTC)},
			   {firstName: "James",lastName: "Goodman", birthDay: time.Date(2012, time.November, 10, 23, 0, 0, 0, time.UTC)},
			   {firstName: "Mike",lastName: "Vazovski", birthDay: time.Date(2012, time.November, 10, 23, 0, 0, 0, time.UTC)},
			   {firstName: "Arnold",lastName: "Shwarzeneger", birthDay: time.Date(2013, time.November, 10, 23, 0, 0, 0, time.UTC)},
			   {firstName: "Jeck",lastName: "Shwarzeneger", birthDay: time.Date(2013, time.November, 10, 23, 0, 0, 0, time.UTC)},
			   },
			   want: People {
				   {firstName: "James",lastName: "Goodman", birthDay: time.Date(2012, time.November, 10, 23, 0, 0, 0, time.UTC)},
				   {firstName: "James",lastName: "Freeman", birthDay: time.Date(2012, time.November, 10, 23, 0, 0, 0, time.UTC)},
				   {firstName: "Mike",lastName: "Vazovski", birthDay: time.Date(2012, time.November, 10, 23, 0, 0, 0, time.UTC)},
				   {firstName: "Arnold",lastName: "Shwarzeneger", birthDay: time.Date(2013, time.November, 10, 23, 0, 0, 0, time.UTC)},
				   {firstName: "Jeck",lastName: "Shwarzeneger", birthDay: time.Date(2013, time.November, 10, 23, 0, 0, 0, time.UTC)},
				   },},
   
	   }
	   for key, test := range tests {
		   test.date.Swap(test.firs,test.second)
		   for i := 0; i < test.date.Len(); i++ {
			   if test.date[i].birthDay!=test.want[i].birthDay && 
			   test.date[i].firstName!=test.want[i].firstName &&
				test.date[i].lastName!=test.want[i].lastName{
				t.Errorf("test name : %s is failed, position %d in data and want is different",key,i)}
		   }
	   }
   }
   
   func TestNewMatrix(t *testing.T) {
	   tests:=map[string]struct{
		   input string
		   want Matrix
		   err error
	   }{
		   "Test One": {input: "1 2 3\n4 5 6",want: Matrix{rows: 2,cols: 3,data: []int{1,2,3,4,5,6}}, err: nil},
		   "Test Two (return exeption)": {input: "1 2 3\n4 5",want: Matrix{rows: 2,cols: 3,data: []int{1,2,3,4,5,6}}, err: errors.New("Rows need to be the same length")},
		   "Test Three(return exeption)": {input: "1 e 3\n4 5 6",want: Matrix{rows: 2,cols: 3,data: []int{1,2,3,4,5,6}}, err: errors.New("invalid syntax")},
	   }
	   for key, test := range tests {
		   gotMatrix,err:=New(test.input)
		   if err == nil {
			   if gotMatrix.cols!=test.want.cols{
			   t.Errorf("Test name: %s - number of cols got: %d, but want:%d",key,gotMatrix.cols,test.want.cols)
			   } 
			   if gotMatrix.rows!=test.want.rows{
			   t.Errorf("Test name: %s - number of rows got: %d, but want:%d",key,gotMatrix.rows,test.want.rows)
			   } 
			   for i, gotnumber := range gotMatrix.data {
				   if gotnumber!=test.want.data[i]{
				   t.Errorf("Test name: %s - element array %d: got%d, but want:%d",key,i,gotMatrix.data[i],test.want.data[i])
				   }
			   }
		   } else if errors.Unwrap(err)==errors.Unwrap(test.err) {
			   continue
		   }  else if errors.Unwrap(err.(*strconv.NumError).Err)==errors.Unwrap(test.err) {
			   continue
		   }else {
			   t.Errorf("Test name: %s ,Invalid exeption %#v , %#v",key,err.(*strconv.NumError).Err, test.err)
		   }
	   }
   }
   
   func TestRows(t *testing.T) {
   
	   tests:=map[string]struct{
		   data Matrix
		   want [][]int
	   }{
		   "Test one": {Matrix{rows: 2,cols: 2,data:[]int {1,2,3,4},},[][]int{{1,2},{3,4}}},
	   }
	   for key, test := range tests {
		   got:=test.data.Rows()
		   for i := 0; i < len(got); i++ {
			   for j := 0; j < len(got[i]); j++ {
				   if got[i][j]!=test.want[i][j]{
					   t.Errorf("Test name: %s is failed, got: %d, want %d",key,got[i][j],test.want[i][j])
				   }
			   }
		   }
	   }
   }
   
   func TestCols(t *testing.T) {
   
	   tests:=map[string]struct{
		   data Matrix
		   want [][]int
	   }{
		   "Test one": {Matrix{rows: 2,cols: 2,data:[]int {1,2,3,4},},[][]int{{1,3},{2,4}}},
	   }
	   for key, test := range tests {
		   got:=test.data.Cols()
		   for i := 0; i < len(got); i++ {
			   for j := 0; j < len(got[i]); j++ {
				   if got[i][j]!=test.want[i][j]{
					   t.Errorf("Test name: %s is failed, got: %d, want %d",key,got[i][j],test.want[i][j])
				   }
			   }
		   }
	   }
   }
   
   func TestSet(t *testing.T) {
	   tests:=map[string]struct{
		   date Matrix
		   wantMatrix [][]int
		   setRow int
		   setCol int
		   setNumber int
		   wantResult bool
	   }{
		   "Test One":{date: Matrix{rows: 2,cols: 2,data:[]int {1,2,3,4},},wantMatrix: [][]int{{10,3},{2,4}},setRow: 0,setCol: 0,setNumber: 10,wantResult: true },
		   "Test two (incorrect coordinates) ":{date: Matrix{rows: 2,cols: 2,data:[]int {1,2,3,4},},wantMatrix: [][]int{{10,3},{2,4}},setRow: 2,setCol: 0,setNumber: 10,wantResult: false },
		   "Test three(incorrect coordinates) ":{date: Matrix{rows: 2,cols: 2,data:[]int {1,2,3,4},},wantMatrix: [][]int{{10,3},{2,4}},setRow: -1,setCol: 0,setNumber: 10,wantResult: false },
		   "Test four(incorrect coordinates) ":{date: Matrix{rows: 2,cols: 2,data:[]int {1,2,3,4},},wantMatrix: [][]int{{10,3},{2,4}},setRow: 0,setCol: 2,setNumber: 10,wantResult: false },
		   "Test five(incorrect coordinates) ":{date: Matrix{rows: 2,cols: 2,data:[]int {1,2,3,4},},wantMatrix: [][]int{{10,3},{2,4}},setRow: 0,setCol: -1,setNumber: 10,wantResult: false },
	   }
	   for key, test := range tests {
		   got:=test.date
		   gotbool := got.Set(test.setRow,test.setCol,test.setNumber)
		   if gotbool{
			   if got.Rows()[test.setRow][test.setRow]!=test.wantMatrix[test.setRow][test.setRow] {
				   t.Error("Tha ha ha")
			   }
   
		   }else{
			   if gotbool !=test.wantResult {
				   t.Errorf("Test name: %s is failed, check bool",key)
			   }
   
		   }
	   }
   }