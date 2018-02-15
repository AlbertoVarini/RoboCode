# RoboCode
package RoboA;
import java.awt.Color;
import robocode.BulletHitBulletEvent;
import robocode.BulletHitEvent;
import robocode.HitByBulletEvent;
import robocode.HitRobotEvent;
import robocode.HitWallEvent;
import robocode.Robot;
import robocode.ScannedRobotEvent;

public class YouRobot extends Robot
{
	public int x,y;
	public double energy;
	public boolean moviment=true;
	public void run()
	{
		setColors(Color.BLACK, Color.BLACK, Color.RED);
		while(true)
		{
			if(moviment)
			{
				ahead(300);
				turnGunRight(360);
				fire(1);
				turnLeft(300);
				turnGunLeft(360);
				back(200);
			}
		}
}
	public void onScannedRobot(ScannedRobotEvent event)
	{
		if(getGunHeat()>110)
		{
			fire(2);
		}
		else
		{
			fire(3);
		}
	}
	public void onBulletHit(BulletHitEvent event)
	{
		fire(2);
	}
	public void onHitByBullet(HitByBulletEvent e)
	{
		for(int i=0;i<2;i++)
		{
			fire(1);
			back(50);
		}
		
	}
	public void onBulletHitBullet(BulletHitBulletEvent event)
	{
		for(int i=0;i<2;i++)
		{
			fire(1);
			back(50);
		}
	}
	public void onHitRobot(HitRobotEvent event)
	{
		for(int i=0;i<4;i++)
		{
			fire(0.5);
			back(50);
		}
	}
	public void onHitWall(HitWallEvent event)
	{
		ahead(50);
		back(50);
		turnRight(300);
		
	}
}
