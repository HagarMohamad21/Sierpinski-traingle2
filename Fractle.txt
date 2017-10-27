#include <GL/glut.h>
#include <math.h>
void display(void)
{

	typedef GLfloat XYcoordinates[2]; 
	XYcoordinates vertices[3] = { { 25.0,25.0 },{ 50.0, 75.0 },{ 75.0,25 } };
	
	int i, j, k;
	XYcoordinates point = { 33,33 };

	glClear(GL_COLOR_BUFFER_BIT);

	

	for (k = 0; k <= 10000; k++)
	{
		j = rand() % 3; 

		point[0] = (point[0] + vertices[j][0]) / 2.0;
		point[1] = (point[1] + vertices[j][1]) / 2.0;
		
		glBegin(GL_POINTS);
		glVertex2fv(point);
		glEnd();
	}
	
	glFlush();
}
void init(void)
{
	/* select clearing color */
	glClearColor(0.0, 0.0, 0.0, 0.0);
	/* initialize viewing values */
	glMatrixMode(GL_PROJECTION);
	glLoadIdentity();
	glOrtho(0.0, 100.0, 0.0, 100.0, -1.0, 1.0);
	glMatrixMode(GL_MODELVIEW);
}

int main(int argc, char** argv)
{
	glutInit(&argc, argv);
	glutInitDisplayMode(GLUT_SINGLE | GLUT_RGB);
	glutInitWindowSize(800, 800);
	glutInitWindowPosition(100, 100);
	glutCreateWindow("Hello OpenGL");
	init();
	glutDisplayFunc(display);
	glutMainLoop();
	return 0; /* ANSI C requires main to return int. */
}