export interface Profile {
  name: string;
  photoUrl: string;
  description: string;
  address: string;
}
import { Profile } from './profile.model';

export const profiles: Profile[] = [
  {
    name: 'John Doe',
    photoUrl: '...',
    description: '...',
    address: '123 Main St, City'
  },
  // Add more profiles...
];
import { Component } from '@angular/core';
import { Profile } from './profile.model';
import { profiles } from './profile-data';

@Component({
  selector: 'app-profile-list',
  templateUrl: './profile-list.component.html',
  styleUrls: ['./profile-list.component.css']
})
export class ProfileListComponent {
  profiles: Profile[] = profiles;
}
<div class="profile-list">
  <div *ngFor="let profile of profiles" class="profile">
    <img [src]="profile.photoUrl" alt="Profile Photo">
    <h2>{{ profile.name }}</h2>
    <p>{{ profile.description }}</p>
    <button (click)="showProfileOnMap(profile)">Summary</button>
  </div>
</div>
import { Component, Input } from '@angular/core';
import { Profile } from './profile.model';

@Component({
  selector: 'app-map',
  templateUrl: './map.component.html',
  styleUrls: ['./map.component.css']
})
export class MapComponent {
  @Input() profile: Profile | undefined;
}
<div class="map-container">
  <div *ngIf="profile" class="map">
    <!-- Use external map service API to display map and marker -->
  </div>
</div>
<div class="app-container">
  <app-profile-list></app-profile-list>
  <app-map [profile]="selectedProfile"></app-map>
</div>
