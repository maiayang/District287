Student data sources used for analyses:

Clean Student Data
1. Student data from Synergy for school sites (ABEC, NEC, WEC, SEC, CTC)-see query below

QUERY for student data from Synergy:
Student R0, K12.EnrollmentInfo.StudentSOREnrollment R1, Revelation.OrganizationInfo.RevOrganizationYear R2 (OrganizationYearGU,R1.OrganizationYearGU,Outer), Revelation.OrganizationInfo.RevOrganization R3 (OrganizationGU,R2.OrganizationGU,Outer)
 COLS R3.OrganizationAbbrName, R0.FormattedName, R0.SisNumber, R1.Grade, R0.Gender, R0.VerboseAge, R0.HomeLanguage, R0.OriginalEnterDate, R1.DistrictOfResidenceDD, R0.StudentGU (hide), R0.EthnicCode, R0.StateEthnicity
 If R3.OrganizationAbbrName Contain ('SEC') Or R3.OrganizationAbbrName Contain ('WEC') Or R3.OrganizationAbbrName Contain ('ABEC') Or R3.OrganizationAbbrName Contain ('NEC') Or R3.OrganizationAbbrName Contain ('W-Alt') Or R3.OrganizationAbbrName Contain ('Gateway') Or R3.OrganizationAbbrName Contain ('CTC')

************************** 

Attendance Analysis
1. Attendance data by student pulled from District Dashboard
2. Cleaned student data 

************************** 

Behavior Analysis (Referrals, RPs)
1. Behavior data by student pulled form District Dashboard
2. Cleaned student data

************************** 

Dispositions Analysis (Suspensions)
1. Dispositions data from Synergy-see query below
2. Cleaned student data 

QUERY for Dispositions data from Synergy:
K12.DisciplineInfo.SchoolIncident R0, K12.Staff R1 (StaffGU,R0.StaffReferredByGU,Outer), K12.DisciplineInfo.StudentIncidentViolation R2, K12.DisciplineInfo.SchoolIncidentLocation R3, K12.DisciplineInfo.StudentIncidentDiscipline R4, K12.DisciplineInfo.SchoolIncident R11 (SchIncidentGU,R2.SchIncidentGU,Outer), K12.DisciplineInfo.StudentIncidentDisposition R5 (StuIncDispositionGU,R4.StuIncDispositionGU,Outer), K12.EnrollmentInfo.StudentSchoolYear R6 (StudentSchoolYearGU,R4.StudentSchoolYearGU,Outer), K12.DisciplineInfo.Setup.DistrictDispositionCode R10 (CodeDispGU,R5.CodeDispGU,Outer), K12.Student R7 (StudentGU,R6.StudentGU,Outer), Revelation.OrganizationInfo.RevOrganizationYear R8 (OrganizationYearGU,R6.OrganizationYearGU,Outer), Revelation.OrganizationInfo.RevOrganization R9 (OrganizationGU,R8.OrganizationGU,Outer)
 COLS R0.IncidentDate, R1.FormattedName (label='Referring Staff'), R1.BadgeNum, R6.AllGradesReadOnly (hide), R8.OrganizationGU (hide), R9.OrganizationAbbrName, R0.IncidentID, R6.StudentGU (hide), R6.OrganizationYearGU (hide), R0.RefferalDate, R0.EnteredByGU (hide), R0.TotalOffenders, R3.Location, R4.IncidentRole, R0.StaffReferredByGU (hide), R4.StudentSchoolYearGU (hide), R0.OffenderName (hide), R0.OffenderSISNumber (hide), R4.Motivation, R0.OffenderStudentGU (hide), R7.FormattedName, R7.SisNumber, R5.Code (hide), R10.Description (label='Disposition';Description), R10.DispCode (hide), R2.ViolationDesc, R7.Gender, R6.Grade, R7.EthnicCode, R7.VerboseAge
 If R10.DispCode Not ='NR100'

************************** 

Reading/Math Assessment Analysis
1. Reading/Math scores by student from District Dashboard